NAME
====

shells - pathnames of valid login shells

DESCRIPTION
===========

*/etc/shells* is a text file which contains the full pathnames of valid
login shells. This file is consulted by **chsh**\ (1) and available to
be queried by other programs.

Be aware that there are programs which consult this file to find out if
a user is a normal user; for example, FTP daemons traditionally disallow
access to users with shells not included in this file.

FILES
=====

*/etc/shells*

EXAMPLES
========

*/etc/shells* may contain the following paths:

::

   /bin/sh
   /bin/bash
   /bin/csh

SEE ALSO
========

**chsh**\ (1), **getusershell**\ (3), **pam_shells**\ (8)
