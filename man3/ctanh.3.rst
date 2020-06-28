NAME
====

ctanh, ctanhf, ctanhl - complex hyperbolic tangent

SYNOPSIS
========

**#include <complex.h>**

| **double complex ctanh(double complex**\ *z*\ **);**
| **float complex ctanhf(float complex**\ *z*\ **);**
| **long double complex ctanhl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex hyperbolic tangent of *z*.

The complex hyperbolic tangent function is defined mathematically as:

::

       ctanh(z) = csinh(z) / ccosh(z)

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============================================= ============= =======
Interface                                     Attribute     Value
**ctanh**\ (), **ctanhf**\ (), **ctanhl**\ () Thread safety MT-Safe
============================================= ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **catanh**\ (3), **ccosh**\ (3), **csinh**\ (3),
**complex**\ (7)
