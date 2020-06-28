NAME
====

strxfrm - string transformation

SYNOPSIS
========

::

   #include <string.h>

   size_t strxfrm(char *dest, const char *src, size_t n);

DESCRIPTION
===========

The **strxfrm**\ () function transforms the *src* string into a form
such that the result of **strcmp**\ (3) on two strings that have been
transformed with **strxfrm**\ () is the same as the result of
**strcoll**\ (3) on the two strings before their transformation. The
first *n* bytes of the transformed string are placed in *dest*. The
transformation is based on the program's current locale for category
**LC_COLLATE**. (See **setlocale**\ (3)).

RETURN VALUE
============

The **strxfrm**\ () function returns the number of bytes required to
store the transformed string in *dest* excluding the terminating null
byte ('\0'). If the value returned is *n* or more, the contents of
*dest* are indeterminate.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= ==============
Interface       Attribute     Value
**strxfrm**\ () Thread safety MT-Safe locale
=============== ============= ==============

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99, SVr4, 4.3BSD.

SEE ALSO
========

**bcmp**\ (3), **memcmp**\ (3), **setlocale**\ (3), **strcasecmp**\ (3),
**strcmp**\ (3), **strcoll**\ (3), **string**\ (3)
