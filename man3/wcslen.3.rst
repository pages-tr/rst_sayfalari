NAME
====

wcslen - determine the length of a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   size_t wcslen(const wchar_t *s);

DESCRIPTION
===========

The **wcslen**\ () function is the wide-character equivalent of the
**strlen**\ (3) function. It determines the length of the wide-character
string pointed to by *s*, excluding the terminating null wide character
(L'\0').

RETURN VALUE
============

The **wcslen**\ () function returns the number of wide characters in
*s*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**wcslen**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strlen**\ (3)
