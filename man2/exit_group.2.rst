NAME
====

exit_group - exit all threads in a process

SYNOPSIS
========

::

   #include <linux/unistd.h>

   void exit_group(int status);

DESCRIPTION
===========

This system call is equivalent to **\_exit**\ (2) except that it
terminates not only the calling thread, but all threads in the calling
process's thread group.

RETURN VALUE
============

This system call does not return.

VERSIONS
========

This call is present since Linux 2.5.35.

CONFORMING TO
=============

This call is Linux-specific.

NOTES
=====

Since glibc 2.3, this is the system call invoked when the
**\_exit**\ (2) wrapper function is called.

SEE ALSO
========

**exit**\ (2)
