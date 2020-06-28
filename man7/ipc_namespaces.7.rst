NAME
====

ipc_namespaces - overview of Linux IPC namespaces

DESCRIPTION
===========

IPC namespaces isolate certain IPC resources, namely, System V IPC
objects (see **sysvipc**\ (7)) and (since Linux 2.6.30) POSIX message
queues (see **mq_overview**\ (7)). The common characteristic of these
IPC mechanisms is that IPC objects are identified by mechanisms other
than filesystem pathnames.

Each IPC namespace has its own set of System V IPC identifiers and its
own POSIX message queue filesystem. Objects created in an IPC namespace
are visible to all other processes that are members of that namespace,
but are not visible to processes in other IPC namespaces.

The following */proc* interfaces are distinct in each IPC namespace:

-  The POSIX message queue interfaces in */proc/sys/fs/mqueue*.

-  The System V IPC interfaces in */proc/sys/kernel*, namely: *msgmax*,
   *msgmnb*, *msgmni*, *sem*, *shmall*, *shmmax*, *shmmni*, and
   *shm_rmid_forced*.

-  The System V IPC interfaces in */proc/sysvipc*.

When an IPC namespace is destroyed (i.e., when the last process that is
a member of the namespace terminates), all IPC objects in the namespace
are automatically destroyed.

Use of IPC namespaces requires a kernel that is configured with the
**CONFIG_IPC_NS** option.

SEE ALSO
========

**nsenter**\ (1), **unshare**\ (1), **clone**\ (2), **setns**\ (2),
**unshare**\ (2), **mq_overview**\ (7), **namespaces**\ (7),
**sysvipc**\ (7)
