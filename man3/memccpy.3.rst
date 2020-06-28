NAME
====

memccpy - copy memory area

SYNOPSIS
========

::

   #include <string.h>

   void *memccpy(void *dest, const void *src, int c, size_t n);

DESCRIPTION
===========

The **memccpy**\ () function copies no more than *n* bytes from memory
area *src* to memory area *dest*, stopping when the character *c* is
found.

If the memory areas overlap, the results are undefined.

RETURN VALUE
============

The **memccpy**\ () function returns a pointer to the next character in
*dest* after *c*, or NULL if *c* was not found in the first *n*
characters of *src*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**memccpy**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SVr4, 4.3BSD.

SEE ALSO
========

**bcopy**\ (3), **bstring**\ (3), **memcpy**\ (3), **memmove**\ (3),
**strcpy**\ (3), **strncpy**\ (3)
