NAME
====

wcsstr - locate a substring in a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcsstr(const wchar_t *haystack, const wchar_t *needle);

DESCRIPTION
===========

The **wcsstr**\ () function is the wide-character equivalent of the
**strstr**\ (3) function. It searches for the first occurrence of the
wide-character string *needle* (without its terminating null wide
character (L'\0')) as a substring in the wide-character string
*haystack*.

RETURN VALUE
============

The **wcsstr**\ () function returns a pointer to the first occurrence of
*needle* in *haystack*. It returns NULL if *needle* does not occur as a
substring in *haystack*.

Note the special case: If *needle* is the empty wide-character string,
the return value is always *haystack* itself.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**wcsstr**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**strstr**\ (3), **wcschr**\ (3)
