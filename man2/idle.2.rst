NAME
====

idle - make process 0 idle

SYNOPSIS
========

**#include <unistd.h>**

**int idle(void);**

DESCRIPTION
===========

**idle**\ () is an internal system call used during bootstrap. It marks
the process's pages as swappable, lowers its priority, and enters the
main scheduling loop. **idle**\ () never returns.

Only process 0 may call **idle**\ (). Any user process, even a process
with superuser permission, will receive **EPERM**.

RETURN VALUE
============

**idle**\ () never returns for process 0, and always returns -1 for a
user process.

ERRORS
======

**EPERM**
   Always, for a user process.

VERSIONS
========

Since Linux 2.3.13, this system call does not exist anymore.

CONFORMING TO
=============

This function is Linux-specific, and should not be used in programs
intended to be portable.
