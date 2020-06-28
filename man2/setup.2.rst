NAME
====

setup - setup devices and filesystems, mount root filesystem

SYNOPSIS
========

**#include <unistd.h>**

**int setup(void);**

DESCRIPTION
===========

**setup**\ () is called once from within *linux/init/main.c*. It calls
initialization functions for devices and filesystems configured into the
kernel and then mounts the root filesystem.

No user process may call **setup**\ (). Any user process, even a process
with superuser permission, will receive **EPERM**.

RETURN VALUE
============

**setup**\ () always returns -1 for a user process.

ERRORS
======

**EPERM**
   Always, for a user process.

VERSIONS
========

Since Linux 2.1.121, no such function exists anymore.

CONFORMING TO
=============

This function is Linux-specific, and should not be used in programs
intended to be portable, or indeed in any programs at all.

NOTES
=====

The calling sequence varied: at some times **setup**\ () has had a
single argument *void \*BIOS* and at other times a single argument *int
magic*.
