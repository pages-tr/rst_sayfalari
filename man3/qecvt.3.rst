NAME
====

qecvt, qfcvt, qgcvt - convert a floating-point number to a string

SYNOPSIS
========

**#include <stdlib.h>**

**char \*qecvt(long double**\ *number*\ **, int**\ *ndigits*\ **, int
\***\ *decpt*\ **,** **int \***\ *sign*\ **);**

**char \*qfcvt(long double**\ *number*\ **, int**\ *ndigits*\ **, int
\***\ *decpt*\ **,** **int \***\ *sign*\ **);**

**char \*qgcvt(long double**\ *number*\ **, int**\ *ndigit*\ **, char
\***\ *buf*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**qecvt**\ (), **qfcvt**\ (), **qgcvt**\ (): \_SVID_SOURCE

DESCRIPTION
===========

The functions **qecvt**\ (), **qfcvt**\ (), and **qgcvt**\ () are
identical to **ecvt**\ (3), **fcvt**\ (3), and **gcvt**\ (3)
respectively, except that they use a *long double* argument *number*.
See **ecvt**\ (3) and **gcvt**\ (3).

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============= ============= ====================
Interface     Attribute     Value
**qecvt**\ () Thread safety MT-Unsafe race:qecvt
**qfcvt**\ () Thread safety MT-Unsafe race:qfcvt
**qgcvt**\ () Thread safety MT-Safe
============= ============= ====================

CONFORMING TO
=============

SVr4. Not seen in most common UNIX implementations, but occurs in SunOS.
Supported by glibc.

NOTES
=====

These functions are obsolete. Instead, **snprintf**\ (3) is recommended.

SEE ALSO
========

**ecvt**\ (3), **ecvt_r**\ (3), **gcvt**\ (3), **sprintf**\ (3)
