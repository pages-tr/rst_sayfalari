NAME
====

unlockpt - unlock a pseudoterminal master/slave pair

SYNOPSIS
========

| **#define \_XOPEN_SOURCE**
| **#include <stdlib.h>**

**int unlockpt(int**\ *fd*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

| **unlockpt**\ ():

   | Since glibc 2.24: \_XOPEN_SOURCE >= 500 \|\| (_XOPEN_SOURCE &&
     \_XOPEN_SOURCE_EXTENDED)
   | Glibc 2.23 and earlier: \_XOPEN_SOURCE

DESCRIPTION
===========

The **unlockpt**\ () function unlocks the slave pseudoterminal device
corresponding to the master pseudoterminal referred to by *fd*.

**unlockpt**\ () should be called before opening the slave side of a
pseudoterminal.

RETURN VALUE
============

When successful, **unlockpt**\ () returns 0. Otherwise, it returns -1
and sets *errno* appropriately.

ERRORS
======

**EBADF**
   The *fd* argument is not a file descriptor open for writing.

**EINVAL**
   The *fd* argument is not associated with a master pseudoterminal.

VERSIONS
========

**unlockpt**\ () is provided in glibc since version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**unlockpt**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**grantpt**\ (3), **posix_openpt**\ (3), **ptsname**\ (3), **pts**\ (4),
**pty**\ (7)
