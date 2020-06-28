NAME
====

putgrent - write a group database entry to a file

SYNOPSIS
========

| **#define \_GNU_SOURCE** /\* See feature_test_macros(7) \*/
| **#include <grp.h>**

**int putgrent(const struct group \***\ *grp*\ **, FILE
\***\ *stream*\ **);**

DESCRIPTION
===========

The **putgrent**\ () function is the counterpart for **fgetgrent**\ (3).
The function writes the content of the provided *struct group* into the
*stream*. The list of group members must be NULL-terminated or
NULL-initialized.

The *struct group* is defined as follows:

::

   struct group {
       char   *gr_name;      /* group name */
       char   *gr_passwd;    /* group password */
       gid_t   gr_gid;       /* group ID */
       char  **gr_mem;       /* group members */
   };

RETURN VALUE
============

The function returns zero on success, and a nonzero value on error.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

================ ============= =======
Interface        Attribute     Value
**putgrent**\ () Thread safety MT-Safe
================ ============= =======

CONFORMING TO
=============

This function is a GNU extension.

SEE ALSO
========

**fgetgrent**\ (3), **getgrent**\ (3), **group**\ (5)
