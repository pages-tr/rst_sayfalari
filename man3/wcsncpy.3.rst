NAME
====

wcsncpy - copy a fixed-size string of wide characters

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcsncpy(wchar_t *dest, const wchar_t *src, size_t n);

DESCRIPTION
===========

The **wcsncpy**\ () function is the wide-character equivalent of the
**strncpy**\ (3) function. It copies at most *n* wide characters from
the wide-character string pointed to by *src*, including the terminating
null wide character (L'\0'), to the array pointed to by *dest*. Exactly
*n* wide characters are written at *dest*. If the length *wcslen(src)*
is smaller than *n*, the remaining wide characters in the array pointed
to by *dest* are filled with null wide characters. If the length
*wcslen(src)* is greater than or equal to *n*, the string pointed to by
*dest* will not be terminated by a null wide character.

The strings may not overlap.

The programmer must ensure that there is room for at least *n* wide
characters at *dest*.

RETURN VALUE
============

**wcsncpy**\ () returns *dest*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**wcsncpy**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strncpy**\ (3)
