NAME
====

ioctl_fslabel - get or set a filesystem label

SYNOPSIS
========

| 
| **#include <sys/ioctl.h>**
| **#include <linux/fs.h>**

| **int ioctl(int**\ *fd*\ **, FS_IOC_GETFSLABEL,
  char**\ *label*\ **[FSLABEL_MAX]);**
| **int ioctl(int**\ *fd*\ **, FS_IOC_SETFSLABEL,
  char**\ *label*\ **[FSLABEL_MAX]);**

DESCRIPTION
===========

If a filesystem supports online label manipulation, these **ioctl**\ (2)
operations can be used to get or set the filesystem label for the
filesystem on which **fd** resides. The **FS_IOC_SETFSLABEL** operation
requires privilege (**CAP_SYS_ADMIN**).

RETURN VALUE
============

On success zero is returned. On error, -1 is returned, and *errno* is
set to indicate the error.

ERRORS
======

Error can include (but are not limited to) the following:

**EFAULT**
   *label* references an inaccessible memory area.

**EINVAL**
   The specified label exceeds the maximum label length for the
   filesystem.

**ENOTTY**
   This can appear if the filesystem does not support online label
   manipulation.

**EPERM**
   The calling process does not have sufficient permissions to set the
   label.

VERSIONS
========

These **ioctl**\ (2) operations first appeared in Linux 4.18. They were
previously known as **BTRFS_IOC_GET_FSLABEL** and
**BTRFS_IOC_SET_FSLABEL** and were private to Btrfs.

CONFORMING TO
=============

This API is Linux-specific.

NOTES
=====

The maximum string length for this interface is **FSLABEL_MAX**,
including the terminating null byte ('\0'). Filesystems have differing
maximum label lengths, which may or may not include the terminating
null. The string provided to **FS_IOC_SETFSLABEL** must always be
null-terminated, and the string returned by **FS_IOC_GETFSLABEL** will
always be null-terminated.

SEE ALSO
========

**ioctl**\ (2), **blkid**\ (8)
