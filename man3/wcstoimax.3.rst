NAME
====

wcstoimax, wcstoumax - convert wide-character string to integer

SYNOPSIS
========

::

   #include <stddef.h>
   #include <inttypes.h>

   intmax_t wcstoimax(const wchar_t *nptr, wchar_t **endptr",int"base);
   uintmax_t wcstoumax(const wchar_t *nptr, wchar_t **endptr",int"base);

DESCRIPTION
===========

These functions are just like **wcstol**\ (3) and **wcstoul**\ (3),
except that they return a value of type *intmax_t* and *uintmax_t*,
respectively.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

==================================== ============= ==============
Interface                            Attribute     Value
**wcstoimax**\ (), **wcstoumax**\ () Thread safety MT-Safe locale
==================================== ============= ==============

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

SEE ALSO
========

**imaxabs**\ (3), **imaxdiv**\ (3), **strtoimax**\ (3),
**strtoumax**\ (3), **wcstol**\ (3), **wcstoul**\ (3)
