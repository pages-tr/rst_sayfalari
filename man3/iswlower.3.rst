NAME
====

iswlower - test for lowercase wide character

SYNOPSIS
========

::

   #include <wctype.h>

   int iswlower(wint_t wc);

DESCRIPTION
===========

The **iswlower**\ () function is the wide-character equivalent of the
**islower**\ (3) function. It tests whether *wc* is a wide character
belonging to the wide-character class "lower".

The wide-character class "lower" is a subclass of the wide-character
class "alpha", and therefore also a subclass of the wide-character class
"alnum", of the wide-character class "graph" and of the wide-character
class "print".

Being a subclass of the wide-character class "print", the wide-character
class "lower" is disjoint from the wide-character class "cntrl".

Being a subclass of the wide-character class "graph", the wide-character
class "lower" is disjoint from the wide-character class "space" and its
subclass "blank".

Being a subclass of the wide-character class "alnum", the wide-character
class "lower" is disjoint from the wide-character class "punct".

Being a subclass of the wide-character class "alpha", the wide-character
class "lower" is disjoint from the wide-character class "digit".

The wide-character class "lower" contains at least those characters *wc*
which are equal to *towlower(wc)* and different from *towupper(wc)*.

The wide-character class "lower" always contains at least the letters
'a' to 'z'.

RETURN VALUE
============

The **iswlower**\ () function returns nonzero if *wc* is a wide
character belonging to the wide-character class "lower". Otherwise, it
returns zero.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= ==============
Interface        Attribute     Value
**iswlower**\ () Thread safety MT-Safe locale
================ ============= ==============

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The behavior of **iswlower**\ () depends on the **LC_CTYPE** category of
the current locale.

This function is not very appropriate for dealing with Unicode
characters, because Unicode knows about three cases: upper, lower and
title case.

SEE ALSO
========

**islower**\ (3), **iswctype**\ (3), **towlower**\ (3)
