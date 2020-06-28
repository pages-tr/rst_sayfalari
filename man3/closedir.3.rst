NAME
====

closedir - close a directory

SYNOPSIS
========

::

   #include <sys/types.h>

   #include <dirent.h>

   int closedir(DIR *dirp);

DESCRIPTION
===========

The **closedir**\ () function closes the directory stream associated
with *dirp*. A successful call to **closedir**\ () also closes the
underlying file descriptor associated with *dirp*. The directory stream
descriptor *dirp* is not available after this call.

RETURN VALUE
============

The **closedir**\ () function returns 0 on success. On error, -1 is
returned, and *errno* is set appropriately.

ERRORS
======

**EBADF**
   Invalid directory stream descriptor *dirp*.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**closedir**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008, SVr4, 4.3BSD.

SEE ALSO
========

**close**\ (2), **opendir**\ (3), **readdir**\ (3), **rewinddir**\ (3),
**scandir**\ (3), **seekdir**\ (3), **telldir**\ (3)
