NAME
====

gnu_get_libc_version, gnu_get_libc_release - get glibc version and
release

SYNOPSIS
========

::

   #include <gnu/libc-version.h>

   const char *gnu_get_libc_version(void);
   const char *gnu_get_libc_release(void);

DESCRIPTION
===========

The function **gnu_get_libc_version**\ () returns a string that
identifies the glibc version available on the system.

The function **gnu_get_libc_release**\ () returns a string indicates the
release status of the glibc version available on the system. This will
be a string such as *stable*.

VERSIONS
========

These functions first appeared in glibc in version 2.1.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

+------------------------------------------+---------------+---------+
| Interface                                | Attribute     | Value   |
+------------------------------------------+---------------+---------+
| **gnu_get_libc_version**\ (),            | Thread safety | MT-Safe |
| **gnu_get_libc_release**\ ()             |               |         |
+------------------------------------------+---------------+---------+

CONFORMING TO
=============

These functions are glibc-specific.

EXAMPLES
========

When run, the program below will produce output such as the following:

::

   $ ./a.out
   GNU libc version: 2.8
   GNU libc release: stable

Program source
--------------

::

   #include <gnu/libc-version.h>
   #include <stdlib.h>
   #include <stdio.h>

   int
   main(int argc, char *argv[])
   {
       printf("GNU libc version: %s\n", gnu_get_libc_version());
       printf("GNU libc release: %s\n", gnu_get_libc_release());
       exit(EXIT_SUCCESS);
   }

SEE ALSO
========

**confstr**\ (3)
