NAME
====

wcsrchr - search a wide character in a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcsrchr(const wchar_t *wcs, wchar_t wc);

DESCRIPTION
===========

The **wcsrchr**\ () function is the wide-character equivalent of the
**strrchr**\ (3) function. It searches the last occurrence of *wc* in
the wide-character string pointed to by *wcs*.

RETURN VALUE
============

The **wcsrchr**\ () function returns a pointer to the last occurrence of
*wc* in the wide-character string pointed to by *wcs*, or NULL if *wc*
does not occur in the string.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**wcsrchr**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strrchr**\ (3), **wcschr**\ (3)
