NAME
====

gcvt - convert a floating-point number to a string

SYNOPSIS
========

::

   #include <stdlib.h>

   char *gcvt(double number, int ndigit, char *buf);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**gcvt**\ ():

   Since glibc 2.12:

   ::

      (_XOPEN_SOURCE >= 500) ! (_POSIX_C_SOURCE >= 200112L)
          || /* Glibc since 2.19: */ _DEFAULT_SOURCE
          || /* Glibc versions <= 2.19: */ _SVID_SOURCE

   Before glibc 2.12:
      \_SVID_SOURCE \|\| \_XOPEN_SOURCE >= 500

DESCRIPTION
===========

The **gcvt**\ () function converts *number* to a minimal length
null-terminated ASCII string and stores the result in *buf*. It produces
*ndigit* significant digits in either **printf**\ (3) F format or E
format.

RETURN VALUE
============

The **gcvt**\ () function returns *buf*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============ ============= =======
Interface    Attribute     Value
**gcvt**\ () Thread safety MT-Safe
============ ============= =======

CONFORMING TO
=============

Marked as LEGACY in POSIX.1-2001. POSIX.1-2008 removes the specification
of **gcvt**\ (), recommending the use of **sprintf**\ (3) instead
(though **snprintf**\ (3) may be preferable).

SEE ALSO
========

**ecvt**\ (3), **fcvt**\ (3), **sprintf**\ (3)
