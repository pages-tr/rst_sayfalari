NAME
====

getloadavg - get system load averages

SYNOPSIS
========

::

   #include <stdlib.h>

   int getloadavg(double loadavg[], int nelem);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**getloadavg**\ ():

::

       Since glibc 2.19:
           _DEFAULT_SOURCE
       In glibc up to and including 2.19:
           _BSD_SOURCE

DESCRIPTION
===========

The **getloadavg**\ () function returns the number of processes in the
system run queue averaged over various periods of time. Up to *nelem*
samples are retrieved and assigned to successive elements of
*loadavg*\ []. The system imposes a maximum of 3 samples, representing
averages over the last 1, 5, and 15 minutes, respectively.

RETURN VALUE
============

If the load average was unobtainable, -1 is returned; otherwise, the
number of samples actually retrieved is returned.

VERSIONS
========

This function is available in glibc since version 2.2.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================== ============= =======
Interface          Attribute     Value
**getloadavg**\ () Thread safety MT-Safe
================== ============= =======

CONFORMING TO
=============

Not in POSIX.1. Present on the BSDs and Solaris.

SEE ALSO
========

**uptime**\ (1), **proc**\ (5)
