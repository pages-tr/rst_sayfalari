NAME
====

dirfd - get directory stream file descriptor

SYNOPSIS
========

| **#include <sys/types.h>**
| **#include <dirent.h>**

**int dirfd(DIR \***\ *dirp*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

| **dirfd**\ ():

   /\* Since glibc 2.10: \*/ \_POSIX_C_SOURCE >= 200809L \|\| /\* Glibc
   versions <= 2.19: \*/ \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

The function **dirfd**\ () returns the file descriptor associated with
the directory stream *dirp*.

This file descriptor is the one used internally by the directory stream.
As a result, it is useful only for functions which do not depend on or
alter the file position, such as **fstat**\ (2) and **fchdir**\ (2). It
will be automatically closed when **closedir**\ (3) is called.

RETURN VALUE
============

On success, **dirfd**\ () returns a file descriptor (a nonnegative
integer). On error, -1 is returned, and *errno* is set to indicate the
cause of the error.

ERRORS
======

POSIX.1-2008 specifies two errors, neither of which is returned by the
current implementation.

**EINVAL**
   *dirp* does not refer to a valid directory stream.

**ENOTSUP**
   The implementation does not support the association of a file
   descriptor with a directory.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============= ============= =======
Interface     Attribute     Value
**dirfd**\ () Thread safety MT-Safe
============= ============= =======

CONFORMING TO
=============

POSIX.1-2008. This function was a BSD extension, present in 4.3BSD-Reno,
not in 4.2BSD.

SEE ALSO
========

**open**\ (2), **openat**\ (2), **closedir**\ (3), **opendir**\ (3),
**readdir**\ (3), **rewinddir**\ (3), **scandir**\ (3),
**seekdir**\ (3), **telldir**\ (3)
