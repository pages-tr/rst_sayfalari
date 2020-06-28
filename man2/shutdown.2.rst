NAME
====

shutdown - shut down part of a full-duplex connection

SYNOPSIS
========

**#include <sys/socket.h>**

**int shutdown(int**\ *sockfd*\ **, int**\ *how*\ **);**

DESCRIPTION
===========

The **shutdown**\ () call causes all or part of a full-duplex connection
on the socket associated with *sockfd* to be shut down. If *how* is
**SHUT_RD**, further receptions will be disallowed. If *how* is
**SHUT_WR**, further transmissions will be disallowed. If *how* is
**SHUT_RDWR**, further receptions and transmissions will be disallowed.

RETURN VALUE
============

On success, zero is returned. On error, -1 is returned, and *errno* is
set appropriately.

ERRORS
======

**EBADF**
   *sockfd* is not a valid file descriptor.

**EINVAL**
   An invalid value was specified in *how* (but see BUGS).

**ENOTCONN**
   The specified socket is not connected.

**ENOTSOCK**
   The file descriptor *sockfd* does not refer to a socket.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, 4.4BSD (**shutdown**\ () first appeared in
4.2BSD).

NOTES
=====

The constants **SHUT_RD**, **SHUT_WR**, **SHUT_RDWR** have the value 0,
1, 2, respectively, and are defined in *<sys/socket.h>* since
glibc-2.1.91.

BUGS
====

Checks for the validity of *how* are done in domain-specific code, and
before Linux 3.7 not all domains performed these checks. Most notably,
UNIX domain sockets simply ignored invalid values. This problem was
fixed for UNIX domain sockets in Linux 3.7.

SEE ALSO
========

**close**\ (2), **connect**\ (2), **socket**\ (2), **socket**\ (7)
