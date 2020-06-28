NAME
====

wmemmove - copy an array of wide-characters

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wmemmove(wchar_t *dest, const wchar_t *src, size_t n);

DESCRIPTION
===========

The **wmemmove**\ () function is the wide-character equivalent of the
**memmove**\ (3) function. It copies *n* wide characters from the array
starting at *src* to the array starting at *dest*. The arrays may
overlap.

The programmer must ensure that there is room for at least *n* wide
characters at *dest*.

RETURN VALUE
============

**wmemmove**\ () returns *dest*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**wmemmove**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**memmove**\ (3), **wmemcpy**\ (3)
