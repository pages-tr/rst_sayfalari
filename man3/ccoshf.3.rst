NAME
====

ccosh, ccoshf, ccoshl - complex hyperbolic cosine

SYNOPSIS
========

**#include <complex.h>**

| **double complex ccosh(double complex**\ *z*\ **);**
| **float complex ccoshf(float complex**\ *z*\ **);**
| **long double complex ccoshl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex hyperbolic cosine of *z*.

The complex hyperbolic cosine function is defined as:

::

       ccosh(z) = (exp(z)+exp(-z))/2

VERSIONS
========

These functions first appeared in glibc in version 2.1.

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **cacosh**\ (3), **csinh**\ (3), **ctanh**\ (3),
**complex**\ (7)
