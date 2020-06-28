NAME
====

tcgetsid - get session ID

SYNOPSIS
========

| **#define \_XOPEN_SOURCE 500** /\* See feature_test_macros(7) \*/
| **#include <termios.h>**

**pid_t tcgetsid(int**\ *fd*\ **);**

DESCRIPTION
===========

The function **tcgetsid**\ () returns the session ID of the current
session that has the terminal associated to *fd* as controlling
terminal. This terminal must be the controlling terminal of the calling
process.

RETURN VALUE
============

When *fd* refers to the controlling terminal of our session, the
function **tcgetsid**\ () will return the session ID of this session.
Otherwise, -1 is returned, and *errno* is set appropriately.

ERRORS
======

**EBADF**
   *fd* is not a valid file descriptor.

**ENOTTY**
   The calling process does not have a controlling terminal, or it has
   one but it is not described by *fd*.

VERSIONS
========

**tcgetsid**\ () is provided in glibc since version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**tcgetsid**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008.

NOTES
=====

This function is implemented via the **TIOCGSID** **ioctl**\ (2),
present since Linux 2.1.71.

SEE ALSO
========

**getsid**\ (2)
