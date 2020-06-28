NAME
====

getdirentries - get directory entries in a filesystem-independent format

SYNOPSIS
========

**#include <dirent.h>**

**ssize_t getdirentries(int**\ *fd*\ **, char \***\ *buf*\ **,
size_t**\ *nbytes* **, off_t \***\ *basep*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**getdirentries**\ (): Since glibc 2.19: \_DEFAULT_SOURCE Glibc 2.19 and
earlier: \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

Read directory entries from the directory specified by *fd* into *buf*.
At most *nbytes* are read. Reading starts at offset *\*basep*, and
*\*basep* is updated with the new position after reading.

RETURN VALUE
============

**getdirentries**\ () returns the number of bytes read or zero when at
the end of the directory. If an error occurs, -1 is returned, and
*errno* is set appropriately.

ERRORS
======

See the Linux library source code for details.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

===================== ============= =======
Interface             Attribute     Value
**getdirentries**\ () Thread safety MT-Safe
===================== ============= =======

CONFORMING TO
=============

Not in POSIX.1. Present on the BSDs, and a few other systems. Use
**opendir**\ (3) and **readdir**\ (3) instead.

SEE ALSO
========

**lseek**\ (2), **open**\ (2)
