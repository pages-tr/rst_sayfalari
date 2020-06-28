NAME
====

copysign, copysignf, copysignl - copy sign of a number

SYNOPSIS
========

::

   #include <math.h>

   double copysign(double x, double y);
   float copysignf(float x, float y);
   long double copysignl(long double x, long double y);

Link with *-lm*.

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**copysign**\ (), **copysignf**\ (), **copysignl**\ ():

   \_ISOC99_SOURCE \|\| \_POSIX_C_SOURCE >= 200112L \|\| /\* Since glibc
   2.19: \*/ \_DEFAULT_SOURCE \|\| /\* Glibc versions <= 2.19: \*/
   \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

These functions return a value whose absolute value matches that of *x*,
but whose sign bit matches that of *y*.

For example, *copysign(42.0, -1.0)* and *copysign(-42.0, -1.0)* both
return -42.0.

RETURN VALUE
============

On success, these functions return a value whose magnitude is taken from
*x* and whose sign is taken from *y*.

If *x* is a NaN, a NaN with the sign bit of *y* is returned.

ERRORS
======

No errors occur.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

+------------------------------------------+---------------+---------+
| Interface                                | Attribute     | Value   |
+------------------------------------------+---------------+---------+
| **copysign**\ (), **copysignf**\ (),     | Thread safety | MT-Safe |
| **copysignl**\ ()                        |               |         |
+------------------------------------------+---------------+---------+

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008. This function is defined in IEC 559
(and the appendix with recommended functions in IEEE 754/IEEE 854).

NOTES
=====

On architectures where the floating-point formats are not IEEE 754
compliant, these functions may treat a negative zero as positive.

SEE ALSO
========

**signbit**\ (3)
