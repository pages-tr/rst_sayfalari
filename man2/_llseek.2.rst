NAME
====

\_llseek - reposition read/write file offset

SYNOPSIS
========

::

   #include <sys/types.h>
   #include <unistd.h>

   int _llseek(unsigned int fd, unsigned long offset_high,
    unsigned long offset_low, loff_t *result,
    unsigned int whence);

*Note*: There is no glibc wrapper for this system call; see NOTES.

DESCRIPTION
===========

The **\_llseek**\ () system call repositions the offset of the open file
description associated with the file descriptor *fd* to
*(offset_high<<32) \| offset_low* bytes relative to the beginning of the
file, the current file offset, or the end of the file, depending on
whether *whence* is **SEEK_SET**, **SEEK_CUR**, or **SEEK_END**,
respectively. It returns the resulting file position in the argument
*result*.

This system call exists on various 32-bit platforms to support seeking
to large file offsets.

RETURN VALUE
============

Upon successful completion, **\_llseek**\ () returns 0. Otherwise, a
value of -1 is returned and *errno* is set to indicate the error.

ERRORS
======

**EBADF**
   *fd* is not an open file descriptor.

**EFAULT**
   Problem with copying results to user space.

**EINVAL**
   *whence* is invalid.

CONFORMING TO
=============

This function is Linux-specific, and should not be used in programs
intended to be portable.

NOTES
=====

Glibc does not provide a wrapper for this system call. To invoke it
directly, use **syscall**\ (2). However, you probably want to use the
**lseek**\ (2) wrapper function instead.

SEE ALSO
========

**lseek**\ (2), **open**\ (2), **lseek64**\ (3)
