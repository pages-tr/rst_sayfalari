NAME
====

csqrt, csqrtf, csqrtl - complex square root

SYNOPSIS
========

**#include <complex.h>**

| **double complex csqrt(double complex**\ *z*\ **);**
| **float complex csqrtf(float complex**\ *z*\ **);**
| **long double complex csqrtl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex square root of *z*, with a branch
cut along the negative real axis. (That means that *csqrt(-1+eps*I)*
will be close to I while *csqrt(-1-eps*I)* will be close to -I, *if eps*
is a small positive real number.)

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============================================= ============= =======
Interface                                     Attribute     Value
**csqrt**\ (), **csqrtf**\ (), **csqrtl**\ () Thread safety MT-Safe
============================================= ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **cexp**\ (3), **complex**\ (7)
