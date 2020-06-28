NAME
====

updwtmp, logwtmp - append an entry to the wtmp file

SYNOPSIS
========

::

   #include <utmp.h>

   void updwtmp(const char *wtmp_file, const struct utmp *ut);
   void logwtmp(const char *line, const char *name",constchar*"host);

For **logwtmp**\ (), link with *-lutil*.

DESCRIPTION
===========

**updwtmp**\ () appends the utmp structure *ut* to the wtmp file.

**logwtmp**\ () constructs a utmp structure using *line*, *name*,
*host*, current time and current process ID. Then it calls
**updwtmp**\ () to append the structure to the wtmp file.

FILES
=====

*/var/log/wtmp*
   database of past user logins

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= ========================
Interface        Attribute     Value
**updwtmp**\ (), Thread safety MT-Unsafe sig:ALRM timer
**logwtmp**\ ()                
================ ============= ========================

CONFORMING TO
=============

Not in POSIX.1. Present on Solaris, NetBSD, and perhaps other systems.

NOTES
=====

For consistency with the other "utmpx" functions (see
**getutxent**\ (3)), glibc provides (since version 2.1):

::

   #include <utmpx.h>
   void updwtmpx (const char *wtmpx_file, const struct utmpx *utx);

This function performs the same task as **updwtmp**\ (), but differs in
that it takes a *utmpx* structure as its last argument.

SEE ALSO
========

**getutxent**\ (3), **wtmp**\ (5)
