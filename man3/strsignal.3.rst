NAME
====

strsignal - return string describing signal

SYNOPSIS
========

::

   #include <string.h>

   char *strsignal(int sig);

   extern const char * const sys_siglist[];

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**strsignal**\ ():

   Since glibc 2.10:
      \_POSIX_C_SOURCE >= 200809L

   Before glibc 2.10:
      \_GNU_SOURCE

DESCRIPTION
===========

The **strsignal**\ () function returns a string describing the signal
number passed in the argument *sig*. The string can be used only until
the next call to **strsignal**\ ().

The array *sys_siglist* holds the signal description strings indexed by
signal number. The **strsignal**\ () function should be used if possible
instead of this array.

RETURN VALUE
============

The **strsignal**\ () function returns the appropriate description
string, or an unknown signal message if the signal number is invalid. On
some systems (but not on Linux), NULL may instead be returned for an
invalid signal number.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================= ============= ===============================
Interface         Attribute     Value
**strsignal**\ () Thread safety MT-Unsafe race:strsignal locale
================= ============= ===============================

CONFORMING TO
=============

POSIX.1-2008. Present on Solaris and the BSDs.

SEE ALSO
========

**psignal**\ (3), **strerror**\ (3)
