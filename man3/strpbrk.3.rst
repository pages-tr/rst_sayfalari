NAME
====

strpbrk - search a string for any of a set of bytes

SYNOPSIS
========

::

   #include <string.h>

   char *strpbrk(const char *s, const char *accept);

DESCRIPTION
===========

The **strpbrk**\ () function locates the first occurrence in the string
*s* of any of the bytes in the string *accept*.

RETURN VALUE
============

The **strpbrk**\ () function returns a pointer to the byte in *s* that
matches one of the bytes in *accept*, or NULL if no such byte is found.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**strpbrk**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99, SVr4, 4.3BSD.

SEE ALSO
========

**index**\ (3), **memchr**\ (3), **rindex**\ (3), **strchr**\ (3),
**string**\ (3), **strsep**\ (3), **strspn**\ (3), **strstr**\ (3),
**strtok**\ (3), **wcspbrk**\ (3)
