NAME
====

swab - swap adjacent bytes

SYNOPSIS
========

::

   #define _XOPEN_SOURCE /* See feature_test_macros(7) */
   #include <unistd.h>

   void swab(const void *from, void *to, ssize_t n);

DESCRIPTION
===========

The **swab**\ () function copies *n* bytes from the array pointed to by
*from* to the array pointed to by *to*, exchanging adjacent even and odd
bytes. This function is used to exchange data between machines that have
different low/high byte ordering.

This function does nothing when *n* is negative. When *n* is positive
and odd, it handles *n-1* bytes as above, and does something unspecified
with the last byte. (In other words, *n* should be even.)

RETURN VALUE
============

The **swab**\ () function returns no value.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============ ============= =======
Interface    Attribute     Value
**swab**\ () Thread safety MT-Safe
============ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SVr4, 4.3BSD.

SEE ALSO
========

**bstring**\ (3)
