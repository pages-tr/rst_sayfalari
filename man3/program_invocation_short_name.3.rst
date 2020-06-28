NAME
====

program_invocation_name, program_invocation_short_name - obtain name
used to invoke calling program

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <errno.h>

   extern char *program_invocation_name;
   extern char *program_invocation_short_name;

DESCRIPTION
===========

*program_invocation_name* contains the name that was used to invoke the
calling program. This is the same as the value of *argv[0]* in
*main*\ (), with the difference that the scope of
*program_invocation_name* is global.

*program_invocation_short_name* contains the basename component of name
that was used to invoke the calling program. That is, it is the same
value as *program_invocation_name*, with all text up to and including
the final slash (/), if any, removed.

These variables are automatically initialized by the glibc run-time
startup code.

CONFORMING TO
=============

These variables are GNU extensions, and should not be used in programs
intended to be portable.

NOTES
=====

The Linux-specific */proc/[number]/cmdline* file provides access to
similar information.

SEE ALSO
========

**proc**\ (5)
