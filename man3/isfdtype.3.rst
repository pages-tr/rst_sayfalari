NAME
====

isfdtype - test file type of a file descriptor

SYNOPSIS
========

::

   #include <sys/stat.h>
   #include <sys/socket.h>

   int isfdtype(int fd, int fdtype);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**isfdtype**\ ():

   Since glibc 2.20:
      \_DEFAULT_SOURCE

   Before glibc 2.20:
      \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

The **isfdtype**\ () function tests whether the file descriptor *fd*
refers to a file of type *fdtype*. The *fdtype* argument specifies one
of the **S_IF\*** constants defined in *<sys/stat.h>* and documented in
**stat**\ (2) (e.g., **S_IFREG**).

RETURN VALUE
============

The **isfdtype**\ () function returns 1 if the file descriptor *fd* is
of type *fdtype* and 0 if it is not. On error, -1 is returned and
*errno* is set to indicate the cause.

ERRORS
======

The **isfdtype**\ () function can fail with any of the same errors as
**fstat**\ (3).

CONFORMING TO
=============

The **isfdtype**\ () function is not specified in any standard, but did
appear in the draft POSIX.1g standard. It is present on OpenBSD and
Tru64 UNIX (where the required header file in both cases is just
*<sys/stat.h>*, as shown in the POSIX.1g draft), and possibly other
systems.

NOTES
=====

Portable applications should use **fstat**\ (3) instead.

SEE ALSO
========

**fstat**\ (3)
