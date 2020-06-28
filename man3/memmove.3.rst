NAME
====

memmove - copy memory area

SYNOPSIS
========

::

   #include <string.h>

   void *memmove(void *dest, const void *src, size_t n);

DESCRIPTION
===========

The **memmove**\ () function copies *n* bytes from memory area *src* to
memory area *dest*. The memory areas may overlap: copying takes place as
though the bytes in *src* are first copied into a temporary array that
does not overlap *src* or *dest*, and the bytes are then copied from the
temporary array to *dest*.

RETURN VALUE
============

The **memmove**\ () function returns a pointer to *dest*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**memmove**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99, SVr4, 4.3BSD.

SEE ALSO
========

**bcopy**\ (3), **bstring**\ (3), **memccpy**\ (3), **memcpy**\ (3),
**strcpy**\ (3), **strncpy**\ (3), **wmemmove**\ (3)
