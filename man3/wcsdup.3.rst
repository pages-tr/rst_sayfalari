NAME
====

wcsdup - duplicate a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   wchar_t *wcsdup(const wchar_t *s);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**wcsdup**\ ():

   Since glibc 2.10:
      \_POSIX_C_SOURCE >= 200809L

   Before glibc 2.10:
      \_GNU_SOURCE

DESCRIPTION
===========

The **wcsdup**\ () function is the wide-character equivalent of the
**strdup**\ (3) function. It allocates and returns a new wide-character
string whose initial contents is a duplicate of the wide-character
string pointed to by *s*.

Memory for the new wide-character string is obtained with
**malloc**\ (3), and should be freed with **free**\ (3).

RETURN VALUE
============

On success, **wcsdup**\ () returns a pointer to the new wide-character
string. On error, it returns NULL, with *errno* set to indicate the
cause of the error.

ERRORS
======

**ENOMEM**
   Insufficient memory available to allocate duplicate string.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**wcsdup**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

POSIX.1-2008. This function is not specified in POSIX.1-2001, and is not
widely available on other systems.

SEE ALSO
========

**strdup**\ (3), **wcscpy**\ (3)
