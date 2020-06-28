NAME
====

MB_LEN_MAX - maximum multibyte length of a character across all locales

SYNOPSIS
========

::

   #include <limits.h>

DESCRIPTION
===========

The **MB_LEN_MAX** macro is the maximum number of bytes needed to
represent a single wide character, in any of the supported locales.

RETURN VALUE
============

A constant integer greater than zero.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The entities **MB_LEN_MAX** and *sizeof(wchar_t)* are totally unrelated.
In glibc, **MB_LEN_MAX** is typically 16 (6 in glibc versions earlier
than 2.2), while *sizeof(wchar_t)* is 4.

SEE ALSO
========

**MB_CUR_MAX**\ (3)
