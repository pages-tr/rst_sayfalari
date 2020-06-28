NAME
====

cabs, cabsf, cabsl - absolute value of a complex number

SYNOPSIS
========

**#include <complex.h>**

| **double cabs(double complex**\ *z*\ **);**
| **float cabsf(float complex**\ *z*\ **);**
| **long double cabsl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions return the absolute value of the complex number *z*. The
result is a real number.

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**cabs**\ (), **cabsf**\ (), **cabsl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

NOTES
=====

The function is actually an alias for *hypot(a, b)* (or, equivalently,
*sqrt(a*a + b*b)*).

SEE ALSO
========

**abs**\ (3), **cimag**\ (3), **hypot**\ (3), **complex**\ (7)
