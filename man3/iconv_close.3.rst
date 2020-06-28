NAME
====

iconv_close - deallocate descriptor for character set conversion

SYNOPSIS
========

::

   #include <iconv.h>

   int iconv_close(iconv_t cd);

DESCRIPTION
===========

The **iconv_close**\ () function deallocates a conversion descriptor
*cd* previously allocated using **iconv_open**\ (3).

RETURN VALUE
============

When successful, the **iconv_close**\ () function returns 0. In case of
error, it sets *errno* and returns -1.

VERSIONS
========

This function is available in glibc since version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=================== ============= =======
Interface           Attribute     Value
**iconv_close**\ () Thread safety MT-Safe
=================== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SUSv2.

SEE ALSO
========

**iconv**\ (3), **iconv_open**\ (3)
