
A list of MAC callbacks registered by AMFI.

```
(lldb) settings set target.max-children-count 512

(lldb) p *mac_policy_list.entries[1].mpc->mpc_ops
(const mac_policy_ops) $6 = {
  mpo_audit_check_postselect = 0x0000000000000000
  mpo_audit_check_preselect = 0x0000000000000000
  mpo_bpfdesc_label_associate = 0x0000000000000000
  mpo_bpfdesc_label_destroy = 0x0000000000000000
  mpo_bpfdesc_label_init = 0x0000000000000000
  mpo_bpfdesc_check_receive = 0x0000000000000000
  mpo_cred_check_label_update_execve = 0xffffff7fa5ec4234 (AppleMobileFileIntegrity`_cred_check_label_update_execve(ucred*, vnode*, long long, vnode*, label*, label*, label*, proc*, void*, unsigned long))
  mpo_cred_check_label_update = 0x0000000000000000
  mpo_cred_check_visible = 0x0000000000000000
  mpo_cred_label_associate_fork = 0x0000000000000000
  mpo_cred_label_associate_kernel = 0x0000000000000000
  mpo_cred_label_associate = 0xffffff7fa5ec423f (AppleMobileFileIntegrity`_cred_label_associate(ucred*, ucred*))
  mpo_cred_label_associate_user = 0x0000000000000000
  mpo_cred_label_destroy = 0xffffff7fa5ec428c (AppleMobileFileIntegrity`_cred_label_destroy(label*))
  mpo_cred_label_externalize_audit = 0x0000000000000000
  mpo_cred_label_externalize = 0x0000000000000000
  mpo_cred_label_init = 0xffffff7fa5ec431c (AppleMobileFileIntegrity`_cred_label_init(label*))
  mpo_cred_label_internalize = 0x0000000000000000
  mpo_cred_label_update_execve = 0xffffff7fa5ec2d72 (AppleMobileFileIntegrity`_cred_label_update_execve(ucred*, ucred*, proc*, vnode*, long long, vnode*, label*, label*, label*, unsigned int*, void*, unsigned long, int*))
  mpo_cred_label_update = 0x0000000000000000
  mpo_devfs_label_associate_device = 0x0000000000000000
  mpo_devfs_label_associate_directory = 0x0000000000000000
  mpo_devfs_label_copy = 0x0000000000000000
  mpo_devfs_label_destroy = 0x0000000000000000
  mpo_devfs_label_init = 0x0000000000000000
  mpo_devfs_label_update = 0x0000000000000000
  mpo_file_check_change_offset = 0x0000000000000000
  mpo_file_check_create = 0x0000000000000000
  mpo_file_check_dup = 0x0000000000000000
  mpo_file_check_fcntl = 0x0000000000000000
  mpo_file_check_get_offset = 0x0000000000000000
  mpo_file_check_get = 0x0000000000000000
  mpo_file_check_inherit = 0x0000000000000000
  mpo_file_check_ioctl = 0x0000000000000000
  mpo_file_check_lock = 0x0000000000000000
  mpo_file_check_mmap_downgrade = 0x0000000000000000
  mpo_file_check_mmap = 0xffffff7fa5ec2b96 (AppleMobileFileIntegrity`_file_check_mmap(ucred*, fileglob*, label*, int, int, unsigned long long, int*))
  mpo_file_check_receive = 0x0000000000000000
  mpo_file_check_set = 0x0000000000000000
  mpo_file_label_init = 0x0000000000000000
  mpo_file_label_destroy = 0x0000000000000000
  mpo_file_label_associate = 0x0000000000000000
  mpo_ifnet_check_label_update = 0x0000000000000000
  mpo_ifnet_check_transmit = 0x0000000000000000
  mpo_ifnet_label_associate = 0x0000000000000000
  mpo_ifnet_label_copy = 0x0000000000000000
  mpo_ifnet_label_destroy = 0x0000000000000000
  mpo_ifnet_label_externalize = 0x0000000000000000
  mpo_ifnet_label_init = 0x0000000000000000
  mpo_ifnet_label_internalize = 0x0000000000000000
  mpo_ifnet_label_update = 0x0000000000000000
  mpo_ifnet_label_recycle = 0x0000000000000000
  mpo_inpcb_check_deliver = 0x0000000000000000
  mpo_inpcb_label_associate = 0x0000000000000000
  mpo_inpcb_label_destroy = 0x0000000000000000
  mpo_inpcb_label_init = 0x0000000000000000
  mpo_inpcb_label_recycle = 0x0000000000000000
  mpo_inpcb_label_update = 0x0000000000000000
  mpo_iokit_check_device = 0x0000000000000000
  mpo_ipq_label_associate = 0x0000000000000000
  mpo_ipq_label_compare = 0x0000000000000000
  mpo_ipq_label_destroy = 0x0000000000000000
  mpo_ipq_label_init = 0x0000000000000000
  mpo_ipq_label_update = 0x0000000000000000
  mpo_file_check_library_validation = 0xffffff7fa5ec4fcb (AppleMobileFileIntegrity`_file_check_library_validation(proc*, fileglob*, long long, long long, unsigned long))
  mpo_vnode_notify_setacl = 0x0000000000000000
  mpo_vnode_notify_setattrlist = 0x0000000000000000
  mpo_vnode_notify_setextattr = 0x0000000000000000
  mpo_vnode_notify_setflags = 0x0000000000000000
  mpo_vnode_notify_setmode = 0x0000000000000000
  mpo_vnode_notify_setowner = 0x0000000000000000
  mpo_vnode_notify_setutimes = 0x0000000000000000
  mpo_vnode_notify_truncate = 0x0000000000000000
  mpo_mbuf_label_associate_bpfdesc = 0x0000000000000000
  mpo_mbuf_label_associate_ifnet = 0x0000000000000000
  mpo_mbuf_label_associate_inpcb = 0x0000000000000000
  mpo_mbuf_label_associate_ipq = 0x0000000000000000
  mpo_mbuf_label_associate_linklayer = 0x0000000000000000
  mpo_mbuf_label_associate_multicast_encap = 0x0000000000000000
  mpo_mbuf_label_associate_netlayer = 0x0000000000000000
  mpo_mbuf_label_associate_socket = 0x0000000000000000
  mpo_mbuf_label_copy = 0x0000000000000000
  mpo_mbuf_label_destroy = 0x0000000000000000
  mpo_mbuf_label_init = 0x0000000000000000
  mpo_mount_check_fsctl = 0x0000000000000000
  mpo_mount_check_getattr = 0x0000000000000000
  mpo_mount_check_label_update = 0x0000000000000000
  mpo_mount_check_mount = 0x0000000000000000
  mpo_mount_check_remount = 0x0000000000000000
  mpo_mount_check_setattr = 0x0000000000000000
  mpo_mount_check_stat = 0x0000000000000000
  mpo_mount_check_umount = 0x0000000000000000
  mpo_mount_label_associate = 0x0000000000000000
  mpo_mount_label_destroy = 0x0000000000000000
  mpo_mount_label_externalize = 0x0000000000000000
  mpo_mount_label_init = 0x0000000000000000
  mpo_mount_label_internalize = 0x0000000000000000
  mpo_netinet_fragment = 0x0000000000000000
  mpo_netinet_icmp_reply = 0x0000000000000000
  mpo_netinet_tcp_reply = 0x0000000000000000
  mpo_pipe_check_ioctl = 0x0000000000000000
  mpo_pipe_check_kqfilter = 0x0000000000000000
  mpo_pipe_check_label_update = 0x0000000000000000
  mpo_pipe_check_read = 0x0000000000000000
  mpo_pipe_check_select = 0x0000000000000000
  mpo_pipe_check_stat = 0x0000000000000000
  mpo_pipe_check_write = 0x0000000000000000
  mpo_pipe_label_associate = 0x0000000000000000
  mpo_pipe_label_copy = 0x0000000000000000
  mpo_pipe_label_destroy = 0x0000000000000000
  mpo_pipe_label_externalize = 0x0000000000000000
  mpo_pipe_label_init = 0x0000000000000000
  mpo_pipe_label_internalize = 0x0000000000000000
  mpo_pipe_label_update = 0x0000000000000000
  mpo_policy_destroy = 0x0000000000000000
  mpo_policy_init = 0x0000000000000000
  mpo_policy_initbsd = 0xffffff7fa5ec5021 (AppleMobileFileIntegrity`_policy_initbsd(mac_policy_conf*))
  mpo_policy_syscall = 0x0000000000000000
  mpo_system_check_sysctlbyname = 0x0000000000000000
  mpo_proc_check_inherit_ipc_ports = 0xffffff7fa5ec4353 (AppleMobileFileIntegrity`_proc_check_inherit_ipc_ports(proc*, vnode*, long long, vnode*, long long, vnode*))
  mpo_vnode_check_rename = 0x0000000000000000
  mpo_kext_check_query = 0x0000000000000000
  mpo_iokit_check_nvram_get = 0x0000000000000000
  mpo_iokit_check_nvram_set = 0x0000000000000000
  mpo_iokit_check_nvram_delete = 0x0000000000000000
  mpo_proc_check_expose_task = 0x0000000000000000
  mpo_proc_check_set_host_special_port = 0x0000000000000000
  mpo_proc_check_set_host_exception_port = 0x0000000000000000
  mpo_exc_action_check_exception_send = 0xffffff7fa5ec2776 (AppleMobileFileIntegrity`amfi_exc_action_check_exception_send(label*, exception_action*, label*))
  mpo_exc_action_label_associate = 0xffffff7fa5ec259c (AppleMobileFileIntegrity`amfi_exc_action_label_associate(exception_action*, label*))
  mpo_exc_action_label_populate = 0xffffff7fa5ec25c0 (AppleMobileFileIntegrity`amfi_exc_action_label_populate(label*, proc*))
  mpo_exc_action_label_destroy = 0xffffff7fa5ec25a2 (AppleMobileFileIntegrity`amfi_exc_action_label_destroy(label*))
  mpo_exc_action_label_init = 0xffffff7fa5ec255a (AppleMobileFileIntegrity`amfi_exc_action_label_init(label*))
  mpo_exc_action_label_update = 0xffffff7fa5ec2724 (AppleMobileFileIntegrity`amfi_exc_action_label_update(exception_action*, label*, label*))
  mpo_vnode_check_trigger_resolve = 0x0000000000000000
  mpo_reserved1 = 0x0000000000000000
  mpo_reserved2 = 0x0000000000000000
  mpo_reserved3 = 0x0000000000000000
  mpo_skywalk_flow_check_connect = 0x0000000000000000
  mpo_skywalk_flow_check_listen = 0x0000000000000000
  mpo_posixsem_check_create = 0x0000000000000000
  mpo_posixsem_check_open = 0x0000000000000000
  mpo_posixsem_check_post = 0x0000000000000000
  mpo_posixsem_check_unlink = 0x0000000000000000
  mpo_posixsem_check_wait = 0x0000000000000000
  mpo_posixsem_label_associate = 0x0000000000000000
  mpo_posixsem_label_destroy = 0x0000000000000000
  mpo_posixsem_label_init = 0x0000000000000000
  mpo_posixshm_check_create = 0x0000000000000000
  mpo_posixshm_check_mmap = 0x0000000000000000
  mpo_posixshm_check_open = 0x0000000000000000
  mpo_posixshm_check_stat = 0x0000000000000000
  mpo_posixshm_check_truncate = 0x0000000000000000
  mpo_posixshm_check_unlink = 0x0000000000000000
  mpo_posixshm_label_associate = 0x0000000000000000
  mpo_posixshm_label_destroy = 0x0000000000000000
  mpo_posixshm_label_init = 0x0000000000000000
  mpo_proc_check_debug = 0x0000000000000000
  mpo_proc_check_fork = 0x0000000000000000
  mpo_proc_check_get_task_name = 0x0000000000000000
  mpo_proc_check_get_task = 0x0000000000000000
  mpo_proc_check_getaudit = 0x0000000000000000
  mpo_proc_check_getauid = 0x0000000000000000
  mpo_proc_check_getlcid = 0x0000000000000000
  mpo_proc_check_mprotect = 0x0000000000000000
  mpo_proc_check_sched = 0x0000000000000000
  mpo_proc_check_setaudit = 0x0000000000000000
  mpo_proc_check_setauid = 0x0000000000000000
  mpo_proc_check_setlcid = 0x0000000000000000
  mpo_proc_check_signal = 0x0000000000000000
  mpo_proc_check_wait = 0x0000000000000000
  mpo_proc_label_destroy = 0x0000000000000000
  mpo_proc_label_init = 0x0000000000000000
  mpo_socket_check_accept = 0x0000000000000000
  mpo_socket_check_accepted = 0x0000000000000000
  mpo_socket_check_bind = 0x0000000000000000
  mpo_socket_check_connect = 0x0000000000000000
  mpo_socket_check_create = 0x0000000000000000
  mpo_socket_check_deliver = 0x0000000000000000
  mpo_socket_check_kqfilter = 0x0000000000000000
  mpo_socket_check_label_update = 0x0000000000000000
  mpo_socket_check_listen = 0x0000000000000000
  mpo_socket_check_receive = 0x0000000000000000
  mpo_socket_check_received = 0x0000000000000000
  mpo_socket_check_select = 0x0000000000000000
  mpo_socket_check_send = 0x0000000000000000
  mpo_socket_check_stat = 0x0000000000000000
  mpo_socket_check_setsockopt = 0x0000000000000000
  mpo_socket_check_getsockopt = 0x0000000000000000
  mpo_socket_label_associate_accept = 0x0000000000000000
  mpo_socket_label_associate = 0x0000000000000000
  mpo_socket_label_copy = 0x0000000000000000
  mpo_socket_label_destroy = 0x0000000000000000
  mpo_socket_label_externalize = 0x0000000000000000
  mpo_socket_label_init = 0x0000000000000000
  mpo_socket_label_internalize = 0x0000000000000000
  mpo_socket_label_update = 0x0000000000000000
  mpo_socketpeer_label_associate_mbuf = 0x0000000000000000
  mpo_socketpeer_label_associate_socket = 0x0000000000000000
  mpo_socketpeer_label_destroy = 0x0000000000000000
  mpo_socketpeer_label_externalize = 0x0000000000000000
  mpo_socketpeer_label_init = 0x0000000000000000
  mpo_system_check_acct = 0x0000000000000000
  mpo_system_check_audit = 0x0000000000000000
  mpo_system_check_auditctl = 0x0000000000000000
  mpo_system_check_auditon = 0x0000000000000000
  mpo_system_check_host_priv = 0x0000000000000000
  mpo_system_check_nfsd = 0x0000000000000000
  mpo_system_check_reboot = 0x0000000000000000
  mpo_system_check_settime = 0x0000000000000000
  mpo_system_check_swapoff = 0x0000000000000000
  mpo_system_check_swapon = 0x0000000000000000
  mpo_socket_check_ioctl = 0x0000000000000000
  mpo_sysvmsg_label_associate = 0x0000000000000000
  mpo_sysvmsg_label_destroy = 0x0000000000000000
  mpo_sysvmsg_label_init = 0x0000000000000000
  mpo_sysvmsg_label_recycle = 0x0000000000000000
  mpo_sysvmsq_check_enqueue = 0x0000000000000000
  mpo_sysvmsq_check_msgrcv = 0x0000000000000000
  mpo_sysvmsq_check_msgrmid = 0x0000000000000000
  mpo_sysvmsq_check_msqctl = 0x0000000000000000
  mpo_sysvmsq_check_msqget = 0x0000000000000000
  mpo_sysvmsq_check_msqrcv = 0x0000000000000000
  mpo_sysvmsq_check_msqsnd = 0x0000000000000000
  mpo_sysvmsq_label_associate = 0x0000000000000000
  mpo_sysvmsq_label_destroy = 0x0000000000000000
  mpo_sysvmsq_label_init = 0x0000000000000000
  mpo_sysvmsq_label_recycle = 0x0000000000000000
  mpo_sysvsem_check_semctl = 0x0000000000000000
  mpo_sysvsem_check_semget = 0x0000000000000000
  mpo_sysvsem_check_semop = 0x0000000000000000
  mpo_sysvsem_label_associate = 0x0000000000000000
  mpo_sysvsem_label_destroy = 0x0000000000000000
  mpo_sysvsem_label_init = 0x0000000000000000
  mpo_sysvsem_label_recycle = 0x0000000000000000
  mpo_sysvshm_check_shmat = 0x0000000000000000
  mpo_sysvshm_check_shmctl = 0x0000000000000000
  mpo_sysvshm_check_shmdt = 0x0000000000000000
  mpo_sysvshm_check_shmget = 0x0000000000000000
  mpo_sysvshm_label_associate = 0x0000000000000000
  mpo_sysvshm_label_destroy = 0x0000000000000000
  mpo_sysvshm_label_init = 0x0000000000000000
  mpo_sysvshm_label_recycle = 0x0000000000000000
  mpo_proc_notify_exit = 0x0000000000000000
  mpo_mount_check_snapshot_revert = 0x0000000000000000
  mpo_vnode_check_getattr = 0x0000000000000000
  mpo_mount_check_snapshot_create = 0x0000000000000000
  mpo_mount_check_snapshot_delete = 0x0000000000000000
  mpo_vnode_check_clone = 0x0000000000000000
  mpo_proc_check_get_cs_info = 0x0000000000000000
  mpo_proc_check_set_cs_info = 0x0000000000000000
  mpo_iokit_check_hid_control = 0x0000000000000000
  mpo_vnode_check_access = 0x0000000000000000
  mpo_vnode_check_chdir = 0x0000000000000000
  mpo_vnode_check_chroot = 0x0000000000000000
  mpo_vnode_check_create = 0x0000000000000000
  mpo_vnode_check_deleteextattr = 0x0000000000000000
  mpo_vnode_check_exchangedata = 0x0000000000000000
  mpo_vnode_check_exec = 0x0000000000000000
  mpo_vnode_check_getattrlist = 0x0000000000000000
  mpo_vnode_check_getextattr = 0x0000000000000000
  mpo_vnode_check_ioctl = 0x0000000000000000
  mpo_vnode_check_kqfilter = 0x0000000000000000
  mpo_vnode_check_label_update = 0x0000000000000000
  mpo_vnode_check_link = 0x0000000000000000
  mpo_vnode_check_listextattr = 0x0000000000000000
  mpo_vnode_check_lookup = 0x0000000000000000
  mpo_vnode_check_open = 0x0000000000000000
  mpo_vnode_check_read = 0x0000000000000000
  mpo_vnode_check_readdir = 0x0000000000000000
  mpo_vnode_check_readlink = 0x0000000000000000
  mpo_vnode_check_rename_from = 0x0000000000000000
  mpo_vnode_check_rename_to = 0x0000000000000000
  mpo_vnode_check_revoke = 0x0000000000000000
  mpo_vnode_check_select = 0x0000000000000000
  mpo_vnode_check_setattrlist = 0x0000000000000000
  mpo_vnode_check_setextattr = 0x0000000000000000
  mpo_vnode_check_setflags = 0x0000000000000000
  mpo_vnode_check_setmode = 0x0000000000000000
  mpo_vnode_check_setowner = 0x0000000000000000
  mpo_vnode_check_setutimes = 0x0000000000000000
  mpo_vnode_check_stat = 0x0000000000000000
  mpo_vnode_check_truncate = 0x0000000000000000
  mpo_vnode_check_unlink = 0x0000000000000000
  mpo_vnode_check_write = 0x0000000000000000
  mpo_vnode_label_associate_devfs = 0x0000000000000000
  mpo_vnode_label_associate_extattr = 0x0000000000000000
  mpo_vnode_label_associate_file = 0x0000000000000000
  mpo_vnode_label_associate_pipe = 0x0000000000000000
  mpo_vnode_label_associate_posixsem = 0x0000000000000000
  mpo_vnode_label_associate_posixshm = 0x0000000000000000
  mpo_vnode_label_associate_singlelabel = 0x0000000000000000
  mpo_vnode_label_associate_socket = 0x0000000000000000
  mpo_vnode_label_copy = 0x0000000000000000
  mpo_vnode_label_destroy = 0x0000000000000000
  mpo_vnode_label_externalize_audit = 0x0000000000000000
  mpo_vnode_label_externalize = 0x0000000000000000
  mpo_vnode_label_init = 0x0000000000000000
  mpo_vnode_label_internalize = 0x0000000000000000
  mpo_vnode_label_recycle = 0x0000000000000000
  mpo_vnode_label_store = 0x0000000000000000
  mpo_vnode_label_update_extattr = 0x0000000000000000
  mpo_vnode_label_update = 0x0000000000000000
  mpo_vnode_notify_create = 0x0000000000000000
  mpo_vnode_check_signature = 0xffffff7fa5ec435b (AppleMobileFileIntegrity`_vnode_check_signature(vnode*, label*, cs_blob*, unsigned int*, unsigned int*, int, char**, unsigned long*))
  mpo_vnode_check_uipc_bind = 0x0000000000000000
  mpo_vnode_check_uipc_connect = 0x0000000000000000
  mpo_proc_check_run_cs_invalid = 0x0000000000000000
  mpo_proc_check_suspend_resume = 0x0000000000000000
  mpo_thread_userret = 0x0000000000000000
  mpo_iokit_check_set_properties = 0x0000000000000000
  mpo_system_check_chud = 0x0000000000000000
  mpo_vnode_check_searchfs = 0x0000000000000000
  mpo_priv_check = 0x0000000000000000
  mpo_priv_grant = 0x0000000000000000
  mpo_proc_check_map_anon = 0x0000000000000000
  mpo_vnode_check_fsgetpath = 0x0000000000000000
  mpo_iokit_check_open = 0x0000000000000000
  mpo_proc_check_ledger = 0x0000000000000000
  mpo_vnode_notify_rename = 0x0000000000000000
  mpo_vnode_check_setacl = 0x0000000000000000
  mpo_vnode_notify_deleteextattr = 0x0000000000000000
  mpo_system_check_kas_info = 0x0000000000000000
  mpo_vnode_check_lookup_preflight = 0x0000000000000000
  mpo_vnode_notify_open = 0x0000000000000000
  mpo_system_check_info = 0x0000000000000000
  mpo_pty_notify_grant = 0x0000000000000000
  mpo_pty_notify_close = 0x0000000000000000
  mpo_vnode_find_sigs = 0x0000000000000000
  mpo_kext_check_load = 0x0000000000000000
  mpo_kext_check_unload = 0x0000000000000000
  mpo_proc_check_proc_info = 0x0000000000000000
  mpo_vnode_notify_link = 0x0000000000000000
  mpo_iokit_check_filter_properties = 0x0000000000000000
  mpo_iokit_check_get_property = 0x0000000000000000
}
```

An example of calling an AMFI MAC callback to verify a code signature.

```
(lldb) bt
* thread #3, name = '0xffffff8036b41758', queue = '0x0', stop reason = breakpoint 1.1
  * frame #0: 0xffffff7fa5ec435b AppleMobileFileIntegrity`_vnode_check_signature(vnode*, label*, cs_blob*, unsigned int*, unsigned int*, int, char**, unsigned long*)
    frame #1: 0xffffff80258b4388 kernel.development`mac_vnode_check_signature(vp=0xffffff803e5ce078, cs_blob=0xffffff803c03ac40, imgp=0xffffff8036a03a00, cs_flags=0xffffff90dd91b2e4, signer_type=0xffffff90dd91b2e8, flags=0) at mac_vfs.c:1122 [opt]
    frame #2: 0xffffff80256c0a21 kernel.development`ubc_cs_blob_add(vp=0xffffff803e5ce078, cputype=16777223, base_offset=<unavailable>, addr=<unavailable>, size=<unavailable>, imgp=0xffffff8036a03a00, flags=<unavailable>, ret_blob=<unavailable>) at ubc_subr.c:3255 [opt]
    frame #3: 0xffffff80256fbc29 kernel.development`parse_machfile [inlined] load_code_signature(lcp=<unavailable>, vp=0xffffff803e5ce078, macho_offset=4096, macho_size=17888, cputype=<unavailable>, result=<unavailable>, imgp=<unavailable>) at mach_loader.c:2438 [opt]
    frame #4: 0xffffff80256fbbe6 kernel.development`parse_machfile(vp=0xffffff803e5ce078, map=0xffffff80383a9200, thread=0xffffff80399b3588, header=0xffffff80b9a27000, file_offset=<unavailable>, macho_size=17888, depth=<unavailable>, aslr_offset=<unavailable>, dyld_aslr_offset=<unavailable>, result=<unavailable>, binresult=<unavailable>, imgp=<unavailable>) at mach_loader.c:1040 [opt]
    frame #5: 0xffffff80256fa624 kernel.development`load_machfile(imgp=0xffffff8036a03a00, header=0xffffff80b9a27000, thread=0xffffff80399b3588, mapp=0xffffff90dd91b980, result=0xffffff90dd91ba40) at mach_loader.c:423 [opt]
    frame #6: 0xffffff802566d1bc kernel.development`exec_mach_imgact(imgp=<unavailable>) at kern_exec.c:963 [opt]
    frame #7: 0xffffff8025673041 kernel.development`exec_activate_image(imgp=0xffffff8036a03a00) at kern_exec.c:1477 [opt]
    frame #8: 0xffffff8025671dcb kernel.development`posix_spawn(ap=0xffffff803a6c76d0, uap=<unavailable>, retval=0xffffff803191b040) at kern_exec.c:2797 [opt]
    frame #9: 0xffffff80257a60ca kernel.development`unix_syscall64(state=<unavailable>) at systemcalls.c:382 [opt]
    frame #10: 0xffffff8025120a36 kernel.development`hndl_unix_scall64 + 22
```

The ```dyld``` loader uses ```F_ADDFILESIGS_RETURN``` to initiate signature verification with a callback to AMFI.

```
    frame #1: 0xffffff8030ab4388 kernel.development`mac_vnode_check_signature(vp=0xffffff804c76e3e0, cs_blob=0xffffff80440458c0, imgp=0x0000000000000000, cs_flags=0xffffff90ea4f3944, signer_type=0xffffff90ea4f3948, flags=0) at mac_vfs.c:1122 [opt]
    frame #2: 0xffffff80308c0a21 kernel.development`ubc_cs_blob_add(vp=0xffffff804c76e3e0, cputype=-1, base_offset=<unavailable>, addr=<unavailable>, size=<unavailable>, imgp=0x0000000000000000, flags=<unavailable>, ret_blob=<unavailable>) at ubc_subr.c:3255 [opt]
    frame #3: 0xffffff8030852993 kernel.development`fcntl_nocancel(p=0xffffff803db166d0, uap=0xffffff8045327000, retval=<unavailable>) at kern_descrip.c:1929 [opt]
    frame #4: 0xffffff80309a60ca kernel.development`unix_syscall64(state=<unavailable>) at systemcalls.c:382 [opt]
    frame #5: 0xffffff8030320a36 kernel.development`hndl_unix_scall64 + 22
    
(lldb) f 3
frame #3: 0xffffff8030852993 kernel.development`fcntl_nocancel(p=0xffffff803db166d0, uap=0xffffff8045327000, retval=<unavailable>) at kern_descrip.c:1929 [opt]

(lldb) p uap->cmd
  (int) $168 = 97
```
