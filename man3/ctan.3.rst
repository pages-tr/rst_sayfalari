NAME
====

ctan, ctanf, ctanl - complex tangent function

SYNOPSIS
========

**#include <complex.h>**

| **double complex ctan(double complex**\ *z*\ **);**
| **float complex ctanf(float complex**\ *z*\ **);**
| **long double complex ctanl(long double complex**\ *z*\ **);**

Link with *-lm*.

DESCRIPTION
===========

These functions calculate the complex tangent of *z*.

The complex tangent function is defined as:

::

       ctan(z) = csin(z) / ccos(z)

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================================== ============= =======
Interface                                  Attribute     Value
**ctan**\ (), **ctanf**\ (), **ctanl**\ () Thread safety MT-Safe
========================================== ============= =======

CONFORMING TO
=============

C99, POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**cabs**\ (3), **catan**\ (3), **ccos**\ (3), **csin**\ (3),
**complex**\ (7)
