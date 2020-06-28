NAME
====

atan, atanf, atanl - arc tangent function

SYNOPSIS
========

::

   #include <math.h>

   double atan(double x);
   float atanf(float x);
   long double atanl( long double x);

Link with *-lm*.

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**atanf**\ (), **atanl**\ ():

   \_ISOC99_SOURCE \|\| \_POSIX_C_SOURCE >= 200112L \|\| /\* Since glibc
   2.19: \*/ \_DEFAULT_SOURCE \|\| /\* Glibc versions <= 2.19: \*/
   \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

These functions calculate the principal value of the arc tangent of *x*;
that is the value whose tangent is *x*.

RETURN VALUE
============

On success, these functions return the principal value of the arc
tangent of *x* in radians; the return value is in the range [-pi/2,
pi/2].

If *x* is a NaN, a NaN is returned.

If *x* is +0 (-0), +0 (-0) is returned.

If *x* is positive infinity (negative infinity), +pi/2 (-pi/2) is
returned.

ERRORS
======

No errors occur.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**atan**\ (), **atanf**\ (), **atanl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

The variant returning *double* also conforms to SVr4, 4.3BSD, C89.

SEE ALSO
========

**acos**\ (3), **asin**\ (3), **atan2**\ (3), **carg**\ (3),
**catan**\ (3), **cos**\ (3), **sin**\ (3), **tan**\ (3)
