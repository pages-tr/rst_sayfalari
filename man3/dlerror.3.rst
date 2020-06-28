NAME
====

dlerror - obtain error diagnostic for functions in the dlopen API

SYNOPSIS
========

**#include <dlfcn.h>**

**char \*dlerror(void);**

Link with *-ldl*.

DESCRIPTION
===========

The **dlerror**\ () function returns a human-readable, null-terminated
string describing the most recent error that occurred from a call to one
of the functions in the dlopen API since the last call to
**dlerror**\ (). The returned string does *not* include a trailing
newline.

**dlerror**\ () returns NULL if no errors have occurred since
initialization or since it was last called.

VERSIONS
========

**dlerror**\ () is present in glibc 2.0 and later.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**dlerror**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001.

NOTES
=====

The message returned by **dlerror**\ () may reside in a statically
allocated buffer that is overwritten by subsequent **dlerror**\ ()
calls.

History
-------

This function is part of the dlopen API, derived from SunOS.

EXAMPLES
========

See **dlopen**\ (3).

SEE ALSO
========

**dladdr**\ (3), **dlinfo**\ (3), **dlopen**\ (3), **dlsym**\ (3)
