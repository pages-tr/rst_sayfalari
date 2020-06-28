NAME
====

mbsrtowcs - convert a multibyte string to a wide-character string

SYNOPSIS
========

::

   #include <wchar.h>

   size_t mbsrtowcs(wchar_t *dest, const char **src,
    size_t len, mbstate_t *ps);

DESCRIPTION
===========

If *dest* is not NULL, the **mbsrtowcs**\ () function converts the
multibyte string *\*src* to a wide-character string starting at *dest*.
At most *len* wide characters are written to *dest*. The shift state
*\*ps* is updated. The conversion is effectively performed by repeatedly
calling *mbrtowc(dest, \*src, n, ps)* where *n* is some positive number,
as long as this call succeeds, and then incrementing *dest* by one and
*\*src* by the number of bytes consumed. The conversion can stop for
three reasons:

1. An invalid multibyte sequence has been encountered. In this case,
   *\*src* is left pointing to the invalid multibyte sequence, *(size_t)
   -1* is returned, and *errno* is set to **EILSEQ**.

2. *len* non-L'\0' wide characters have been stored at *dest*. In this
   case, *\*src* is left pointing to the next multibyte sequence to be
   converted, and the number of wide characters written to *dest* is
   returned.

3. The multibyte string has been completely converted, including the
   terminating null wide character ('\0'), which has the side effect of
   bringing back *\*ps* to the initial state. In this case, *\*src* is
   set to NULL, and the number of wide characters written to *dest*,
   excluding the terminating null wide character, is returned.

If *dest* is NULL, *len* is ignored, and the conversion proceeds as
above, except that the converted wide characters are not written out to
memory, and that no length limit exists.

In both of the above cases, if *ps* is NULL, a static anonymous state
known only to the **mbsrtowcs**\ () function is used instead.

The programmer must ensure that there is room for at least *len* wide
characters at *dest*.

RETURN VALUE
============

The **mbsrtowcs**\ () function returns the number of wide characters
that make up the converted part of the wide-character string, not
including the terminating null wide character. If an invalid multibyte
sequence was encountered, *(size_t) -1* is returned, and *errno* set to
**EILSEQ**.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================= ============= ============================
Interface         Attribute     Value
**mbsrtowcs**\ () Thread safety MT-Unsafe race:mbsrtowcs/!ps
================= ============= ============================

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The behavior of **mbsrtowcs**\ () depends on the **LC_CTYPE** category
of the current locale.

Passing NULL as *ps* is not multithread safe.

SEE ALSO
========

**iconv**\ (3), **mbrtowc**\ (3), **mbsinit**\ (3), **mbsnrtowcs**\ (3),
**mbstowcs**\ (3)
