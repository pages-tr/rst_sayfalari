NAME
====

mbrlen - determine number of bytes in next multibyte character

SYNOPSIS
========

::

   #include <wchar.h>

   size_t mbrlen(const char *s, size_t n, mbstate_t *ps);

DESCRIPTION
===========

The **mbrlen**\ () function inspects at most *n* bytes of the multibyte
string starting at *s* and extracts the next complete multibyte
character. It updates the shift state *\*ps*. If the multibyte character
is not the null wide character, it returns the number of bytes that were
consumed from *s*. If the multibyte character is the null wide
character, it resets the shift state *\*ps* to the initial state and
returns 0.

If the *n* bytes starting at *s* do not contain a complete multibyte
character, **mbrlen**\ () returns *(size_t) -2*. This can happen even if
*n* >= *MB_CUR_MAX*, if the multibyte string contains redundant shift
sequences.

If the multibyte string starting at *s* contains an invalid multibyte
sequence before the next complete character, **mbrlen**\ () returns
*(size_t) -1* and sets *errno* to **EILSEQ**. In this case, the effects
on *\*ps* are undefined.

If *ps* is NULL, a static anonymous state known only to the
**mbrlen**\ () function is used instead.

RETURN VALUE
============

The **mbrlen**\ () function returns the number of bytes parsed from the
multibyte sequence starting at *s*, if a non-null wide character was
recognized. It returns 0, if a null wide character was recognized. It
returns *(size_t) -1* and sets *errno* to **EILSEQ**, if an invalid
multibyte sequence was encountered. It returns *(size_t) -2* if it
couldn't parse a complete multibyte character, meaning that *n* should
be increased.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

============== ============= =========================
Interface      Attribute     Value
**mbrlen**\ () Thread safety MT-Unsafe race:mbrlen/!ps
============== ============= =========================

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, C99.

NOTES
=====

The behavior of **mbrlen**\ () depends on the **LC_CTYPE** category of
the current locale.

SEE ALSO
========

**mbrtowc**\ (3)
