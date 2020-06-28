NAME
====

isatty - test whether a file descriptor refers to a terminal

SYNOPSIS
========

::

   #include <unistd.h>

   int isatty(int fd);

DESCRIPTION
===========

The **isatty**\ () function tests whether *fd* is an open file
descriptor referring to a terminal.

RETURN VALUE
============

**isatty**\ () returns 1 if *fd* is an open file descriptor referring to
a terminal; otherwise 0 is returned, and *errno* is set to indicate the
error.

ERRORS
======

**EBADF**
   *fd* is not a valid file descriptor.

**ENOTTY**
   *fd* refers to a file other than a terminal. On some older kernels,
   some types of files resulted in the error **EINVAL** in this case
   (which is a violation of POSIX, which specifies the error
   **ENOTTY**).

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**isatty**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SVr4, 4.3BSD.

SEE ALSO
========

**fstat**\ (2), **ttyname**\ (3)
