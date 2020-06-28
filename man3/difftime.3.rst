NAME
====

difftime - calculate time difference

SYNOPSIS
========

::

   #include <time.h>

   double difftime(time_t time1, time_t time0);

DESCRIPTION
===========

The **difftime**\ () function returns the number of seconds elapsed
between time *time1* and time *time0*, represented as a *double*. Each
of the times is specified in calendar time, which means its value is a
measurement (in seconds) relative to the Epoch, 1970-01-01 00:00:00
+0000 (UTC).

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**difftime**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C89, C99, SVr4, 4.3BSD.

NOTES
=====

On a POSIX system, *time_t* is an arithmetic type, and one could just
define

::

   #define difftime(t1,t0) (double)(t1 - t0)

when the possible overflow in the subtraction is not a concern.

SEE ALSO
========

**date**\ (1), **gettimeofday**\ (2), **time**\ (2), **ctime**\ (3),
**gmtime**\ (3), **localtime**\ (3)
