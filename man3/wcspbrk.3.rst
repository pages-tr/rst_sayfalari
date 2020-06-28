NAME
====

wcspbrk - search a wide-character string for any of a set of wide
characters

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcspbrk(const wchar_t *wcs, const wchar_t *accept);

DESCRIPTION
===========

The **wcspbrk**\ () function is the wide-character equivalent of the
**strpbrk**\ (3) function. It searches for the first occurrence in the
wide-character string pointed to by *wcs* of any of the characters in
the wide-character string pointed to by *accept*.

RETURN VALUE
============

The **wcspbrk**\ () function returns a pointer to the first occurrence
in *wcs* of any of the characters listed in *accept*. If *wcs* contains
none of these characters, NULL is returned.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**wcspbrk**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strpbrk**\ (3), **wcschr**\ (3), **wcscspn**\ (3)
