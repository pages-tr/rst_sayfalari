NAME
====

ccos, ccosf, ccosl - complex cosine function

SYNOPSIS
========

**#include <complex.h>**

| **double complex ccos(double complex**\ *z*\ **);**
| **float complex ccosf(float complex**\ *z*\ **);**
| **long double complex ccosl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex cosine of *z*.

The complex cosine function is defined as:

::

       ccos(z) = (exp(i * z) + exp(-i * z)) / 2

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**ccos**\ (), **ccosf**\ (), **ccosl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **cacos**\ (3), **csin**\ (3), **ctan**\ (3),
**complex**\ (7)
