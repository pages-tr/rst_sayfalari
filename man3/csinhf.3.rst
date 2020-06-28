NAME
====

csinh, csinhf, csinhl - complex hyperbolic sine

SYNOPSIS
========

**#include <complex.h>**

| **double complex csinh(double complex**\ *z*\ **);**
| **float complex csinhf(float complex**\ *z*\ **);**
| **long double complex csinhl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex hyperbolic sine of *z*.

The complex hyperbolic sine function is defined as:

::

       csinh(z) = (exp(z)-exp(-z))/2

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============================================= ============= =======
Interface                                     Attribute     Value
**csinh**\ (), **csinhf**\ (), **csinhl**\ () Thread safety MT-Safe
============================================= ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **casinh**\ (3), **ccosh**\ (3), **ctanh**\ (3),
**complex**\ (7)
