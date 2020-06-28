NAME
====

strfry - randomize a string

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <string.h>

   char *strfry(char *string);

DESCRIPTION
===========

The **strfry**\ () function randomizes the contents of *string* by
randomly swapping characters in the string. The result is an anagram of
*string*.

RETURN VALUE
============

The **strfry**\ () functions returns a pointer to the randomized string.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =======
Interface      Attribute     Value
**strfry**\ () Thread safety MT-Safe
============== ============= =======

CONFORMING TO
=============

The **strfry**\ () function is unique to the GNU C Library.

SEE ALSO
========

**memfrob**\ (3), **string**\ (3)
