NAME
====

fcloseall - close all open streams

SYNOPSIS
========

::

   #define _GNU_SOURCE /* See feature_test_macros(7) */
   #include <stdio.h>

   int fcloseall(void);

DESCRIPTION
===========

The **fcloseall**\ () function closes all of the calling process's open
streams. Buffered output for each stream is written before it is closed
(as for **fflush**\ (3)); buffered input is discarded.

The standard streams, *stdin*, *stdout*, and *stderr* are also closed.

RETURN VALUE
============

This function returns 0 if all files were successfully closed; on error,
**EOF** is returned.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================= ============= ======================
Interface         Attribute     Value
**fcloseall**\ () Thread safety MT-Unsafe race:streams
================= ============= ======================

The **fcloseall**\ () function does not lock the streams, so it is not
thread-safe.

CONFORMING TO
=============

This function is a GNU extension.

SEE ALSO
========

**close**\ (2), **fclose**\ (3), **fflush**\ (3), **fopen**\ (3),
**setbuf**\ (3)
