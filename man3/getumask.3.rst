NAME
====

getumask - get file creation mask

SYNOPSIS
========

| **#define \_GNU_SOURCE** /\* See feature_test_macros(7) \*/
| **#include <sys/types.h>**
| **#include <sys/stat.h>**

**mode_t getumask(void);**

DESCRIPTION
===========

This function returns the current file creation mask. It is equivalent
to

::

   mode_t getumask(void)
   {
       mode_t mask = umask( 0 );
       umask(mask);
       return mask;
   }

except that it is documented to be thread-safe (that is, shares a lock
with the **umask**\ (2) library call).

CONFORMING TO
=============

This is a vaporware GNU extension.

NOTES
=====

This function is documented in the glibc manual, but, as at glibc
version 2.24, it is not implemented on Linux. (See **umask**\ (2) for a
thread-safe method of discovering a process's umask.)

SEE ALSO
========

**umask**\ (2)
