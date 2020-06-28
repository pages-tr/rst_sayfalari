NAME
====

wmemcpy - copy an array of wide-characters

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wmemcpy(wchar_t *dest, const wchar_t *src, size_t n);

DESCRIPTION
===========

The **wmemcpy**\ () function is the wide-character equivalent of the
**memcpy**\ (3) function. It copies *n* wide characters from the array
starting at *src* to the array starting at *dest*.

The arrays may not overlap; use **wmemmove**\ (3) to copy between
overlapping arrays.

The programmer must ensure that there is room for at least *n* wide
characters at *dest*.

RETURN VALUE
============

**wmemcpy**\ () returns *dest*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**wmemcpy**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**memcpy**\ (3), **wcscpy**\ (3), **wmemmove**\ (3), **wmempcpy**\ (3)
