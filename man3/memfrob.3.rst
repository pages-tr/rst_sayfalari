NAME
====

memfrob - frobnicate (encrypt) a memory area

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <string.h>

   void *memfrob(void *s, size_t n);

DESCRIPTION
===========

The **memfrob**\ () function encrypts the first *n* bytes of the memory
area *s* by exclusive-ORing each character with the number 42. The
effect can be reversed by using **memfrob**\ () on the encrypted memory
area.

Note that this function is not a proper encryption routine as the XOR
constant is fixed, and is suitable only for hiding strings.

RETURN VALUE
============

The **memfrob**\ () function returns a pointer to the encrypted memory
area.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**memfrob**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

The **memfrob**\ () function is unique to the GNU C Library.

SEE ALSO
========

**bstring**\ (3), **strfry**\ (3)
