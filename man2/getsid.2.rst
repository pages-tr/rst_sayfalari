NAME
====

getsid - get session ID

SYNOPSIS
========

| **#include <sys/types.h>**
| **#include <unistd.h>**

**pid_t getsid(pid_t**\ *pid*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**getsid**\ ():

   | \_XOPEN_SOURCE >= 500
   | \|\| /\* Since glibc 2.12: \*/ \_POSIX_C_SOURCE >= 200809L

DESCRIPTION
===========

*getsid(0)* returns the session ID of the calling process.
**getsid**\ () returns the session ID of the process with process ID
*pid*. If *pid* is 0, **getsid**\ () returns the session ID of the
calling process.

RETURN VALUE
============

On success, a session ID is returned. On error, *(pid_t) -1* will be
returned, and *errno* is set appropriately.

ERRORS
======

**EPERM**
   A process with process ID *pid* exists, but it is not in the same
   session as the calling process, and the implementation considers this
   an error.

**ESRCH**
   No process with process ID *pid* was found.

VERSIONS
========

This system call is available on Linux since version 2.0.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SVr4.

NOTES
=====

Linux does not return **EPERM**.

See **credentials**\ (7) for a description of sessions and session IDs.

SEE ALSO
========

**getpgid**\ (2), **setsid**\ (2), **credentials**\ (7)
