NAME
====

raise - send a signal to the caller

SYNOPSIS
========

::

   #include <signal.h>

   int raise(int sig);

DESCRIPTION
===========

The **raise**\ () function sends a signal to the calling process or
thread. In a single-threaded program it is equivalent to

::

   kill(getpid(), sig);

In a multithreaded program it is equivalent to

::

   pthread_kill(pthread_self(), sig);

If the signal causes a handler to be called, **raise**\ () will return
only after the signal handler has returned.

RETURN VALUE
============

**raise**\ () returns 0 on success, and nonzero for failure.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============= ============= =======
Interface     Attribute     Value
**raise**\ () Thread safety MT-Safe
============= ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99.

NOTES
=====

Since version 2.3.3, glibc implements **raise**\ () by calling
**tgkill**\ (2), if the kernel supports that system call. Older glibc
versions implemented **raise**\ () using **kill**\ (2).

SEE ALSO
========

**getpid**\ (2), **kill**\ (2), **sigaction**\ (2), **signal**\ (2),
**pthread_kill**\ (3), **signal**\ (7)
