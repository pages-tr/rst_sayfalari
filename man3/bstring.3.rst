NAME
====

bcmp, bcopy, bzero, memccpy, memchr, memcmp, memcpy, memfrob, memmem,
memmove, memset - byte string operations

SYNOPSIS
========

::

   #include <string.h>

   int bcmp(const void *s1, const void *s2, size_t n);

   void bcopy(const void *src, void *dest, size_t n);

   void bzero(void *s, size_t n);

   void *memccpy(void *dest, const void *src, int c, size_t n);

   void *memchr(const void *s, int c, size_t n);

   int memcmp(const void *s1, const void *s2, size_t n);

   void *memcpy(void *dest, const void *src, size_t n);

   void *memfrob(void *s, size_t n);

   void *memmem(const void *haystack, size_t haystacklen,
    const void *needle, size_t needlelen);

   void *memmove(void *dest, const void *src, size_t n);

   void *memset(void *s, int c, size_t n);

DESCRIPTION
===========

The byte string functions perform operations on strings (byte arrays)
that are not necessarily null-terminated. See the individual man pages
for descriptions of each function.

NOTES
=====

The functions **bcmp**\ (), **bcopy**\ () and **bzero**\ () are
obsolete. Use **memcmp**\ (), **memcpy**\ () and **memset**\ () instead.

SEE ALSO
========

**bcmp**\ (3), **bcopy**\ (3), **bzero**\ (3), **memccpy**\ (3),
**memchr**\ (3), **memcmp**\ (3), **memcpy**\ (3), **memfrob**\ (3),
**memmem**\ (3), **memmove**\ (3), **memset**\ (3)
