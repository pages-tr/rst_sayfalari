NAME
====

cimag, cimagf, cimagl - get imaginary part of a complex number

SYNOPSIS
========

**#include <complex.h>**

| **double cimag(double complex**\ *z*\ **);**
| **float cimagf(float complex**\ *z*\ **);**
| **long double cimagl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions return the imaginary part of the complex number *z*.

One has:

::

       z = creal(z) + I * cimag(z)

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============================================= ============= =======
Interface                                     Attribute     Value
**cimag**\ (), **cimagf**\ (), **cimagl**\ () Thread safety MT-Safe
============================================= ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

NOTES
=====

gcc also supports \__imag__. That is a GNU extension.

SEE ALSO
========

**cabs**\ (3), **creal**\ (3), **complex**\ (7)
