NAME
====

getpt - open the pseudoterminal master (PTM)

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <stdlib.h>

   int getpt(void);

DESCRIPTION
===========

**getpt**\ () opens a pseudoterminal master and returns its file
descriptor. It is equivalent to

::

   open("/dev/ptmx", O_RDWR);

on Linux systems, though the pseudoterminal master is located elsewhere
on some systems that use GNU Libc.

RETURN VALUE
============

**getpt**\ () returns an open file descriptor upon successful
completion. Otherwise, it returns -1 and sets *errno* to indicate the
error.

ERRORS
======

**getpt**\ () can fail with various errors described in **open**\ (2).

VERSIONS
========

**getpt**\ () is provided in glibc since version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============= ============= =======
Interface     Attribute     Value
**getpt**\ () Thread safety MT-Safe
============= ============= =======

CONFORMING TO
=============

**getpt**\ () is glibc-specific; use **posix_openpt**\ (3) instead.

SEE ALSO
========

**grantpt**\ (3), **posix_openpt**\ (3), **ptsname**\ (3),
**unlockpt**\ (3), **ptmx**\ (4), **pty**\ (7)
