NAME
====

tkill, tgkill - send a signal to a thread

SYNOPSIS
========

::

   int tkill(int tid, int sig);

   int tgkill(int tgid, int tid, int sig);

*Note*: There is no glibc wrapper for **tkill**\ (); see NOTES.

DESCRIPTION
===========

**tgkill**\ () sends the signal *sig* to the thread with the thread ID
*tid* in the thread group *tgid*. (By contrast, **kill**\ (2) can be
used to send a signal only to a process (i.e., thread group) as a whole,
and the signal will be delivered to an arbitrary thread within that
process.)

**tkill**\ () is an obsolete predecessor to **tgkill**\ (). It allows
only the target thread ID to be specified, which may result in the wrong
thread being signaled if a thread terminates and its thread ID is
recycled. Avoid using this system call.

These are the raw system call interfaces, meant for internal thread
library use.

RETURN VALUE
============

On success, zero is returned. On error, -1 is returned, and *errno* is
set appropriately.

ERRORS
======

**EAGAIN**
   The **RLIMIT_SIGPENDING** resource limit was reached and *sig* is a
   real-time signal.

**EAGAIN**
   Insufficient kernel memory was available and *sig* is a real-time
   signal.

**EINVAL**
   An invalid thread ID, thread group ID, or signal was specified.

**EPERM**
   Permission denied. For the required permissions, see **kill**\ (2).

**ESRCH**
   No process with the specified thread ID (and thread group ID) exists.

VERSIONS
========

**tkill**\ () is supported since Linux 2.4.19 / 2.5.4. **tgkill**\ ()
was added in Linux 2.5.75.

Library support for **tgkill**\ () was added to glibc in version 2.30.

CONFORMING TO
=============

**tkill**\ () and **tgkill**\ () are Linux-specific and should not be
used in programs that are intended to be portable.

NOTES
=====

See the description of **CLONE_THREAD** in **clone**\ (2) for an
explanation of thread groups.

Glibc does not provide a wrapper for **tkill**\ (); call it using
**syscall**\ (2). Before glibc 2.30, there was also no wrapper function
for **tgkill**\ ().

SEE ALSO
========

**clone**\ (2), **gettid**\ (2), **kill**\ (2), **rt_sigqueueinfo**\ (2)
