NAME
====

strlen - calculate the length of a string

SYNOPSIS
========

::

   #include <string.h>

   size_t strlen(const char *s);

DESCRIPTION
===========

The **strlen**\ () function calculates the length of the string pointed
to by *s*, excluding the terminating null byte ('\0').

RETURN VALUE
============

The **strlen**\ () function returns the number of bytes in the string
pointed to by *s*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**strlen**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99, C11, SVr4, 4.3BSD.

SEE ALSO
========

**string**\ (3), **strnlen**\ (3), **wcslen**\ (3), **wcsnlen**\ (3)
