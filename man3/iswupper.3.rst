NAME
====

iswupper - test for uppercase wide character

SYNOPSIS
========

::

   #include <wctype.h>

   int iswupper(wint_t wc);

DESCRIPTION
===========

The **iswupper**\ () function is the wide-character equivalent of the
**isupper**\ (3) function. It tests whether *wc* is a wide character
belonging to the wide-character class "upper".

The wide-character class "upper" is a subclass of the wide-character
class "alpha", and therefore also a subclass of the wide-character class
"alnum", of the wide-character class "graph" and of the wide-character
class "print".

Being a subclass of the wide-character class "print", the wide-character
class "upper" is disjoint from the wide-character class "cntrl".

Being a subclass of the wide-character class "graph", the wide-character
class "upper" is disjoint from the wide-character class "space" and its
subclass "blank".

Being a subclass of the wide-character class "alnum", the wide-character
class "upper" is disjoint from the wide-character class "punct".

Being a subclass of the wide-character class "alpha", the wide-character
class "upper" is disjoint from the wide-character class "digit".

The wide-character class "upper" contains at least those characters *wc*
which are equal to *towupper(wc)* and different from *towlower(wc)*.

The wide-character class "upper" always contains at least the letters
'A' to 'Z'.

RETURN VALUE
============

The **iswupper**\ () function returns nonzero if *wc* is a wide
character belonging to the wide-character class "upper". Otherwise, it
returns zero.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= ==============
Interface        Attribute     Value
**iswupper**\ () Thread safety MT-Safe locale
================ ============= ==============

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The behavior of **iswupper**\ () depends on the **LC_CTYPE** category of
the current locale.

This function is not very appropriate for dealing with Unicode
characters, because Unicode knows about three cases: upper, lower and
title case.

SEE ALSO
========

**isupper**\ (3), **iswctype**\ (3), **towupper**\ (3)
