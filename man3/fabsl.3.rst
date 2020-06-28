NAME
====

fabs, fabsf, fabsl - absolute value of floating-point number

SYNOPSIS
========

::

   #include <math.h>

   double fabs(double x);
   float fabsf(float x);
   long double fabsl(long double x);

Link with *-lm*.

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**fabsf**\ (), **fabsl**\ ():

   \_ISOC99_SOURCE \|\| \_POSIX_C_SOURCE >= 200112L \|\| /\* Since glibc
   2.19: \*/ \_DEFAULT_SOURCE \|\| /\* Glibc versions <= 2.19: \*/
   \_BSD_SOURCE \|\| \_SVID_SOURCE

DESCRIPTION
===========

These functions return the absolute value of the floating-point number
*x*.

RETURN VALUE
============

These functions return the absolute value of *x*.

If *x* is a NaN, a NaN is returned.

If *x* is -0, +0 is returned.

If *x* is negative infinity or positive infinity, positive infinity is
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
**fabs**\ (), **fabsf**\ (), **fabsl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

The variant returning *double* also conforms to SVr4, 4.3BSD, C89.

SEE ALSO
========

**abs**\ (3), **cabs**\ (3), **ceil**\ (3), **floor**\ (3),
**labs**\ (3), **rint**\ (3)
