NAME
====

strstr, strcasestr - locate a substring

SYNOPSIS
========

::

   #include <string.h>

   char *strstr(const char *haystack, const char *needle);

   #define _GNU_SOURCE /* See feature_test_macros(7) */

   #include <string.h>

   char *strcasestr(const char *haystack, const char *needle);

DESCRIPTION
===========

The **strstr**\ () function finds the first occurrence of the substring
*needle* in the string *haystack*. The terminating null bytes ('\0') are
not compared.

The **strcasestr**\ () function is like **strstr**\ (), but ignores the
case of both arguments.

RETURN VALUE
============

These functions return a pointer to the beginning of the located
substring, or NULL if the substring is not found.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================== ============= ==============
Interface          Attribute     Value
**strstr**\ ()     Thread safety MT-Safe
**strcasestr**\ () Thread safety MT-Safe locale
================== ============= ==============

CONFORMING TO
=============

**strstr**\ (): POSIX.1-2001, POSIX.1-2008, C89, C99.

The **strcasestr**\ () function is a nonstandard extension.

SEE ALSO
========

**index**\ (3), **memchr**\ (3), **memmem**\ (3), **rindex**\ (3),
**strcasecmp**\ (3), **strchr**\ (3), **string**\ (3), **strpbrk**\ (3),
**strsep**\ (3), **strspn**\ (3), **strtok**\ (3), **wcsstr**\ (3)
