NAME
====

wcscpy - copy a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcscpy(wchar_t *dest, const wchar_t *src);

DESCRIPTION
===========

The **wcscpy**\ () function is the wide-character equivalent of the
**strcpy**\ (3) function. It copies the wide-character string pointed to
by *src*, including the terminating null wide character (L'\0'), to the
array pointed to by *dest*.

The strings may not overlap.

The programmer must ensure that there is room for at least
*wcslen(src)+1* wide characters at *dest*.

RETURN VALUE
============

**wcscpy**\ () returns *dest*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**wcscpy**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strcpy**\ (3), **wcpcpy**\ (3), **wcscat**\ (3), **wcsdup**\ (3),
**wmemcpy**\ (3)
