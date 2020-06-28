NAME
====

vmsplice - splice user pages to/from a pipe

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <fcntl.h>
   #include <sys/uio.h>

   ssize_t vmsplice(int fd, const struct iovec *iov,
    unsigned long nr_segs, unsigned int flags);

DESCRIPTION
===========

If *fd* is opened for writing, the **vmsplice**\ () system call maps
*nr_segs* ranges of user memory described by *iov* into a pipe. If *fd*
is opened for reading, the **vmsplice**\ () system call fills *nr_segs*
ranges of user memory described by *iov* from a pipe. The file
descriptor *fd* must refer to a pipe.

The pointer *iov* points to an array of *iovec* structures as defined in
*<sys/uio.h>*:

::

   struct iovec {
       void  *iov_base;        /* Starting address */
       size_t iov_len;         /* Number of bytes */
   };

The *flags* argument is a bit mask that is composed by ORing together
zero or more of the following values:

**SPLICE_F_MOVE**
   Unused for **vmsplice**\ (); see **splice**\ (2).

**SPLICE_F_NONBLOCK**
   Do not block on I/O; see **splice**\ (2) for further details.

**SPLICE_F_MORE**
   Currently has no effect for **vmsplice**\ (), but may be implemented
   in the future; see **splice**\ (2).

**SPLICE_F_GIFT**
   The user pages are a gift to the kernel. The application may not
   modify this memory ever, otherwise the page cache and on-disk data
   may differ. Gifting pages to the kernel means that a subsequent
   **splice**\ (2) **SPLICE_F_MOVE** can successfully move the pages; if
   this flag is not specified, then a subsequent **splice**\ (2)
   **SPLICE_F_MOVE** must copy the pages. Data must also be properly
   page aligned, both in memory and length.

RETURN VALUE
============

Upon successful completion, **vmsplice**\ () returns the number of bytes
transferred to the pipe. On error, **vmsplice**\ () returns -1 and
*errno* is set to indicate the error.

ERRORS
======

**EAGAIN**
   **SPLICE_F_NONBLOCK** was specified in *flags*, and the operation
   would block.

**EBADF**
   *fd* either not valid, or doesn't refer to a pipe.

**EINVAL**
   *nr_segs* is greater than **IOV_MAX**; or memory not aligned if
   **SPLICE_F_GIFT** set.

**ENOMEM**
   Out of memory.

VERSIONS
========

The **vmsplice**\ () system call first appeared in Linux 2.6.17; library
support was added to glibc in version 2.5.

CONFORMING TO
=============

This system call is Linux-specific.

NOTES
=====

**vmsplice**\ () follows the other vectorized read/write type functions
when it comes to limitations on the number of segments being passed in.
This limit is **IOV_MAX** as defined in *<limits.h>*. Currently, this
limit is 1024.

**vmsplice**\ () really supports true splicing only from user memory to
a pipe. In the opposite direction, it actually just copies the data to
userspace. But this makes the interface nice and symmetric and enables
people to build on **vmsplice**\ () with room for future improvement in
performance.

SEE ALSO
========

**splice**\ (2), **tee**\ (2), **pipe**\ (7)
