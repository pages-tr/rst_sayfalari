NAME
====

wcsnlen - determine the length of a fixed-size wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   size_t wcsnlen(const wchar_t *s, size_t maxlen);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**wcsnlen**\ ():

   Since glibc 2.10:
      \_POSIX_C_SOURCE >= 200809L

   Before glibc 2.10:
      \_GNU_SOURCE

DESCRIPTION
===========

The **wcsnlen**\ () function is the wide-character equivalent of the
**strnlen**\ (3) function. It returns the number of wide-characters in
the string pointed to by *s*, not including the terminating null wide
character (L'\0'), but at most *maxlen* wide characters (note: this
parameter is not a byte count). In doing this, **wcsnlen**\ () looks at
only the first *maxlen* wide characters at *s* and never beyond
*s+maxlen*.

RETURN VALUE
============

The **wcsnlen**\ () function returns *wcslen(s)*, if that is less than
*maxlen*, or *maxlen* if there is no null wide character among the first
*maxlen* wide characters pointed to by *s*.

VERSIONS
========

The **wcsnlen**\ () function is provided in glibc since version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**wcsnlen**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2008.

SEE ALSO
========

**strnlen**\ (3), **wcslen**\ (3)
