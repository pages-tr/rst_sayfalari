NAME
====

cexp, cexpf, cexpl - complex exponential function

SYNOPSIS
========

**#include <complex.h>**

| **double complex cexp(double complex**\ *z*\ **);**
| **float complex cexpf(float complex**\ *z*\ **);**
| **long double complex cexpl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate e (2.71828..., the base of natural logarithms)
raised to the power of *z*.

One has:

::

       cexp(I * z) = ccos(z) + I * csin(z)

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**cexp**\ (), **cexpf**\ (), **cexpl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **cexp2**\ (3), **clog**\ (3), **cpow**\ (3),
**complex**\ (7)
