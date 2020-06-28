NAME
====

uts_namespaces - overview of Linux UTS namespaces

DESCRIPTION
===========

UTS namespaces provide isolation of two system identifiers: the hostname
and the NIS domain name. These identifiers are set using
**sethostname**\ (2) and **setdomainname**\ (2), and can be retrieved
using **uname**\ (2), **gethostname**\ (2), and **getdomainname**\ (2).
Changes made to these identifiers are visible to all other processes in
the same UTS namespace, but are not visible to processes in other UTS
namespaces.

When a process creates a new UTS namespace using **clone**\ (2) or
**unshare**\ (2) with the **CLONE_NEWUTS** flag, the hostname and domain
of the new UTS namespace are copied from the corresponding values in the
caller's UTS namespace.

Use of UTS namespaces requires a kernel that is configured with the
**CONFIG_UTS_NS** option.

SEE ALSO
========

**nsenter**\ (1), **unshare**\ (1), **clone**\ (2),
**getdomainname**\ (2), **gethostname**\ (2), **setns**\ (2),
**uname**\ (2), **unshare**\ (2), **namespaces**\ (7)
