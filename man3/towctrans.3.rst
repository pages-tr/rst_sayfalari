NAME
====

towctrans - wide-character transliteration

SYNOPSIS
========

::

   #include <wctype.h>

   wint_t towctrans(wint_t wc, wctrans_t desc);

DESCRIPTION
===========

If *wc* is a wide character, the **towctrans**\ () function translates
it according to the transliteration descriptor *desc*. If *wc* is
**WEOF**, **WEOF** is returned.

*desc* must be a transliteration descriptor returned by the
**wctrans**\ (3) function.

RETURN VALUE
============

The **towctrans**\ () function returns the translated wide character, or
**WEOF** if *wc* is **WEOF**.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================= ============= =======
Interface         Attribute     Value
**towctrans**\ () Thread safety MT-Safe
================= ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The behavior of **towctrans**\ () depends on the **LC_CTYPE** category
of the current locale.

SEE ALSO
========

**towlower**\ (3), **towupper**\ (3), **wctrans**\ (3)
