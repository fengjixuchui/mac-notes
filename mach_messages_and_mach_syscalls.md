
Mach system calls are implemented by passing a message from a user mode to a kernel mode with a call to ```mach_msg```.

Below is a call stack for a mach message passing from a user mode stub to a kernel mode server function. A stub and a server are generated by the MIG compiler from *.def files. A server stub in the kernel usually has an _X prefix before a name of a function being called by a server (```kext_request``` in the example below).

```
frame #7: kernel.development`::kext_request(hostPriv=<unavailable>, clientLogSpec=4082, requestIn=<unavailable>, requestLengthIn=<unavailable>, responseOut=0xffffff8023b9a9ac, responseLengthOut=0xffffff8023b9a9d4, logDataOut=<unavailable>, logDataLengthOut=<unavailable>, op_result=<unavailable>) at OSKextLib.cpp:280 [opt]
frame #8: kernel.development`_Xkext_request(InHeadP=<unavailable>, OutHeadP=0xffffff8023b9a988) at host_priv_server.c:2785 [opt]
frame #9:  kernel.development`ipc_kobject_server(request=0xffffff802311a400, option=<unavailable>) at ipc_kobject.c:351 [opt]
frame #10: kernel.development`ipc_kmsg_send(kmsg=0xffffff802311a400, option=3, send_timeout=0) at ipc_kmsg.c:1867 [opt]
frame #11: kernel.development`mach_msg_overwrite_trap(args=<unavailable>) at mach_msg.c:570 [opt]
frame #12: kernel.development`mach_call_munger64(state=0xffffff8022a24d40) at bsd_i386.c:573 [opt]
frame #13: kernel.development`hndl_mach_scall64 + 22
```

The second example is for a semaphore creation
```
* frame #0: 0xffffff80007a5c36 kernel.development`semaphore_create(task=0xffffff800e77c1b8, new_semaphore=0xffffff90a37e3da0, policy=0, value=0) at sync_sema.c:168 [opt]
frame #1: 0xffffff80007f5b9b kernel.development`_Xsemaphore_create(InHeadP=0xffffff8010da4e8c, OutHeadP=0xffffff8010da4788) at task_server.c:2461 [opt]
frame #2: 0xffffff8000781d07 kernel.development`ipc_kobject_server(request=0xffffff8010da4e00, option=<unavailable>) at ipc_kobject.c:351 [opt]
frame #3: 0xffffff8000754d0d kernel.development`ipc_kmsg_send(kmsg=0xffffff8010da4e00, option=3, send_timeout=0) at ipc_kmsg.c:1867 [opt]
frame #4: 0xffffff800076fafb kernel.development`mach_msg_overwrite_trap(args=<unavailable>) at mach_msg.c:570 [opt]
frame #5: 0xffffff80008be0ea kernel.development`mach_call_munger64(state=0xffffff801906e100) at bsd_i386.c:573 [opt]
frame #6: 0xffffff8000720a56 kernel.development`hndl_mach_scall64 + 22
```

Let's look at some functions in the stack.

```mach_msg_overwrite_trap``` copies a message from a user space to a kernel space with a call to ```ipc_kmsg_get``` and resolves port rights to port objects with a call to ```ipc_kmsg_copyin```.

```
mach_msg_return_t
mach_msg_overwrite_trap(
	struct mach_msg_overwrite_trap_args *args)
{
    mach_vm_address_t	msg_addr = args->msg;
    mach_msg_option_t	option = args->option;
    mach_msg_size_t		send_size = args->send_size;
    mach_msg_size_t		rcv_size = args->rcv_size;
    mach_port_name_t	rcv_name = args->rcv_name;
    mach_msg_timeout_t	msg_timeout = args->timeout;
    mach_msg_priority_t override = args->override;
    mach_vm_address_t	rcv_msg_addr = args->rcv_msg;
    __unused mach_port_seqno_t temp_seqno = 0;

    mach_msg_return_t  mr = MACH_MSG_SUCCESS;
    vm_map_t map = current_map();

    /* Only accept options allowed by the user */
    option &= MACH_MSG_OPTION_USER;

    if (option & MACH_SEND_MSG) {
        ipc_space_t space = current_space();
        ipc_kmsg_t kmsg;

        KDBG(MACHDBG_CODE(DBG_MACH_IPC,MACH_IPC_KMSG_INFO) | DBG_FUNC_START);

        mr = ipc_kmsg_get(msg_addr, send_size, &kmsg);
        ...
        mr = ipc_kmsg_copyin(kmsg, space, map, override, &option);
        ...
        mr = ipc_kmsg_send(kmsg, option, msg_timeout);
        ...
    }
}
```

Note that the IPC space for port rights is retrieved from the current task.

```
#define	current_space_fast()	(current_task_fast()->itk_space)
#define current_space()		(current_space_fast())
```

```ipc_kmsg_get``` allocates a kernel message buffer and copies a message data from a user space.

```
mach_msg_return_t
ipc_kmsg_get(
	mach_vm_address_t	msg_addr,
	mach_msg_size_t	size,
	ipc_kmsg_t		*kmsgp)
{
    mach_msg_size_t			msg_and_trailer_size;
    ipc_kmsg_t 			kmsg;
    mach_msg_max_trailer_t	 	*trailer;
    mach_msg_legacy_base_t	    legacy_base;
    mach_msg_size_t             len_copied;
    legacy_base.body.msgh_descriptor_count = 0;

    ...
    if (copyinmsg(msg_addr, (char *)&legacy_base, len_copied))
      return MACH_SEND_INVALID_DATA;

    ...

    msg_and_trailer_size = size + MAX_TRAILER_SIZE;
    kmsg = ipc_kmsg_alloc(msg_and_trailer_size);
    if (kmsg == IKM_NULL)
      return MACH_SEND_NO_BUFFER;

    kmsg->ikm_header->msgh_size			= size;
    kmsg->ikm_header->msgh_bits			= legacy_base.header.msgh_bits;
    kmsg->ikm_header->msgh_remote_port	= CAST_MACH_NAME_TO_PORT(legacy_base.header.msgh_remote_port);
    kmsg->ikm_header->msgh_local_port	= CAST_MACH_NAME_TO_PORT(legacy_base.header.msgh_local_port);
    kmsg->ikm_header->msgh_voucher_port		= legacy_base.header.msgh_voucher_port;
    kmsg->ikm_header->msgh_id			= legacy_base.header.msgh_id;

    ...

    if (copyinmsg(msg_addr, (char *)(kmsg->ikm_header + 1), size - (mach_msg_size_t)sizeof(mach_msg_header_t))) {
      ipc_kmsg_free(kmsg);
      return MACH_SEND_INVALID_DATA;
    }
}
```

Where ```copyinmsg``` is a macro.
```
#define copyinmsg(from, to, cnt)							\
	copyin(from, to, cnt)
```

```ipc_kmsg_copyin``` calls ```ipc_kmsg_copyin_header``` to resolve port rights and ```ipc_kmsg_copyin_body``` to copy an out-of-line memory.

```
mach_msg_return_t
ipc_kmsg_copyin(
	ipc_kmsg_t		kmsg,
	ipc_space_t		space,
	vm_map_t		map,
	mach_msg_priority_t override,
	mach_msg_option_t	*optionp)
{
    mach_msg_return_t 		mr;
    ...
    mr = ipc_kmsg_copyin_header(kmsg, space, override, optionp);
    ...
    mr = ipc_kmsg_copyin_body( kmsg, space, map);
    ...
}
```

```ipc_kmsg_copyin_header``` resolves ports rights to port names and then to port objects.

```
mach_msg_return_t
ipc_kmsg_copyin_header(
	ipc_kmsg_t              kmsg,
	ipc_space_t		space,
	mach_msg_priority_t override,
	mach_msg_option_t	*optionp)
{
  ....
  dest_entry = ipc_entry_lookup(space, dest_name);
  ...
  kr = ipc_right_copyin_two(space, dest_name, dest_entry,
          dest_type, reply_type,
          &dest_port, &dest_soright,
          &release_port);
}
```


```ipc_kobject_server``` uses the ```mig_buckets``` hash table to locate a server stub descriptor and calls its ```ptr->routine```.

```
ipc_kmsg_t
ipc_kobject_server(
	ipc_kmsg_t	request,
	mach_msg_option_t __unused option)
{
	mach_msg_size_t reply_size;
	ipc_kmsg_t reply;
	kern_return_t kr;
	ipc_port_t *destp;
	ipc_port_t  replyp = IPC_PORT_NULL;
	mach_msg_format_0_trailer_t *trailer;
	mig_hash_t *ptr;
	task_t task = TASK_NULL;
	uint32_t exec_token;
	boolean_t exec_token_changed = FALSE;

	/*
	 * Find out corresponding mig_hash entry if any
	 */
	{
	    int key = request->ikm_header->msgh_id;
	    unsigned int i = (unsigned int)MIG_HASH(key);
	    int max_iter = mig_table_max_displ;

	    do {
		    ptr = &mig_buckets[i++ % MAX_MIG_ENTRIES];
	    } while (key != ptr->num && ptr->num && --max_iter);
      ....
	    }
	}
  ...
  (*ptr->routine)(request->ikm_header, reply->ikm_header);
  ...
}
```

The ```mig_buckets``` hash table are generated at the system initialization from MIG compiler generated tables.

```
void
mig_init(void)
{
    unsigned int i, n = sizeof(mig_e)/sizeof(const struct mig_subsystem *);
    int howmany;
    mach_msg_id_t j, pos, nentry, range;
	
    for (i = 0; i < n; i++) {
	range = mig_e[i]->end - mig_e[i]->start;
	if (!mig_e[i]->start || range < 0)
	    panic("the msgh_ids in mig_e[] aren't valid!");

	for  (j = 0; j < range; j++) {
	  if (mig_e[i]->routine[j].stub_routine) { 
	    /* Only put real entries in the table */
	    nentry = j + mig_e[i]->start;	
	    for (pos = MIG_HASH(nentry) % MAX_MIG_ENTRIES, howmany = 1;
		 mig_buckets[pos].num;
		 pos++, pos = pos % MAX_MIG_ENTRIES, howmany++) {
	         if (mig_buckets[pos].num == nentry) {
		        printf("message id = %d\n", nentry);
		 	panic("multiple entries with the same msgh_id");
	         }
		 if (howmany == MAX_MIG_ENTRIES)
		       panic("the mig dispatch table is too small");
	    }
		
	    mig_buckets[pos].num = nentry;
	    mig_buckets[pos].routine = mig_e[i]->routine[j].stub_routine;
	    if (mig_e[i]->routine[j].max_reply_msg)
		    mig_buckets[pos].size = mig_e[i]->routine[j].max_reply_msg;
	    else
		    mig_buckets[pos].size = mig_e[i]->maxsize;

	    mig_table_max_displ = max(howmany, mig_table_max_displ);
	  }
	}
    }
    printf("mig_table_max_displ = %d\n", mig_table_max_displ);
}
```


