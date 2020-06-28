NAME
====

conj, conjf, conjl - calculate the complex conjugate

SYNOPSIS
========

**#include <complex.h>**

| **double complex conj(double complex**\ *z*\ **);**
| **float complex conjf(float complex**\ *z*\ **);**
| **long double complex conjl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions return the complex conjugate value of *z*. That is the
value obtained by changing the sign of the imaginary part.

One has:

::

       cabs(z) = csqrt(z * conj(z))

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**conj**\ (), **conjf**\ (), **conjl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **csqrt**\ (3), **complex**\ (7)
