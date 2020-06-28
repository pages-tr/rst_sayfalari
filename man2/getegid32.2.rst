NAME
====

getgid, getegid - get group identity

SYNOPSIS
========

| **#include <unistd.h>**
| **#include <sys/types.h>**

| **gid_t getgid(void);**
| **gid_t getegid(void);**

DESCRIPTION
===========

**getgid**\ () returns the real group ID of the calling process.

**getegid**\ () returns the effective group ID of the calling process.

ERRORS
======

These functions are always successful.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, 4.3BSD.

NOTES
=====

The original Linux **getgid**\ () and **getegid**\ () system calls
supported only 16-bit group IDs. Subsequently, Linux 2.4 added
**getgid32**\ () and **getegid32**\ (), supporting 32-bit IDs. The glibc
**getgid**\ () and **getegid**\ () wrapper functions transparently deal
with the variations across kernel versions.

On Alpha, instead of a pair of **getgid**\ () and **getegid**\ () system
calls, a single **getxgid**\ () system call is provided, which returns a
pair of real and effective GIDs. The glibc **getgid**\ () and
**getegid**\ () wrapper functions transparently deal with this. See
**syscall**\ (2) for details regarding register mapping.

SEE ALSO
========

**getresgid**\ (2), **setgid**\ (2), **setregid**\ (2),
**credentials**\ (7)
