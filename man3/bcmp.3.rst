NAME
====

bcmp - compare byte sequences

SYNOPSIS
========

::

   #include <strings.h>

   int bcmp(const void *s1, const void *s2, size_t n);

DESCRIPTION
===========

The **bcmp**\ () function compares the two byte sequences *s1* and *s2*
of length *n* each. If they are equal, and in particular if *n* is zero,
**bcmp**\ () returns 0. Otherwise, it returns a nonzero result.

RETURN VALUE
============

The **bcmp**\ () function returns 0 if the byte sequences are equal,
otherwise a nonzero result is returned.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============ ============= =======
Interface    Attribute     Value
**bcmp**\ () Thread safety MT-Safe
============ ============= =======

CONFORMING TO
=============

4.3BSD. This function is deprecated (marked as LEGACY in POSIX.1-2001):
use **memcmp**\ (3) in new programs. POSIX.1-2008 removes the
specification of **bcmp**\ ().

SEE ALSO
========

**bstring**\ (3), **memcmp**\ (3), **strcasecmp**\ (3), **strcmp**\ (3),
**strcoll**\ (3), **strncasecmp**\ (3), **strncmp**\ (3)
