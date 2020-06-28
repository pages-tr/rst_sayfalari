NAME
====

ram - ram disk device

DESCRIPTION
===========

The *ram* device is a block device to access the ram disk in raw mode.

It is typically created by:

::

   mknod -m 660 /dev/ram b 1 1
   chown root:disk /dev/ram

FILES
=====

*/dev/ram*

SEE ALSO
========

**chown**\ (1), **mknod**\ (1), **mount**\ (8)
