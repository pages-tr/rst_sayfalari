NAME
====

ctermid - get controlling terminal name

SYNOPSIS
========

::

   #include <stdio.h>

   char *ctermid(char *s);

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**ctermid**\ (): \_POSIX_C_SOURCE

DESCRIPTION
===========

**ctermid**\ () returns a string which is the pathname for the current
controlling terminal for this process. If *s* is NULL, a static buffer
is used, otherwise *s* points to a buffer used to hold the terminal
pathname. The symbolic constant **L_ctermid** is the maximum number of
characters in the returned pathname.

RETURN VALUE
============

The pointer to the pathname.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

=============== ============= =======
Interface       Attribute     Value
**ctermid**\ () Thread safety MT-Safe
=============== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, Svr4.

BUGS
====

The returned pathname may not uniquely identify the controlling
terminal; it may, for example, be */dev/tty*.

It is not assured that the program can open the terminal.

SEE ALSO
========

**ttyname**\ (3)
