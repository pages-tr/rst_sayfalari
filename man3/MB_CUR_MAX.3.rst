NAME
====

MB_CUR_MAX - maximum length of a multibyte character in the current
locale

SYNOPSIS
========

::

   #include <stdlib.h>

DESCRIPTION
===========

The **MB_CUR_MAX** macro defines an integer expression giving the
maximum number of bytes needed to represent a single wide character in
the current locale. This value is locale dependent and therefore not a
compile-time constant.

RETURN VALUE
============

An integer in the range [1, **MB_LEN_MAX**]. The value 1 denotes
traditional 8-bit encoded characters.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**MB_LEN_MAX**\ (3), **mblen**\ (3), **mbstowcs**\ (3), **mbtowc**\ (3),
**wcstombs**\ (3), **wctomb**\ (3)
