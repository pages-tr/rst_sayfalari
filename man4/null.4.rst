NAME
====

null, zero - data sink

DESCRIPTION
===========

Data written to the */dev/null* and */dev/zero* special files is
discarded.

Reads from */dev/null* always return end of file (i.e., **read**\ (2)
returns 0), whereas reads from */dev/zero* always return bytes
containing zero ('\0' characters).

These devices are typically created by:

::

   mknod -m 666 /dev/null c 1 3
   mknod -m 666 /dev/zero c 1 5
   chown root:root /dev/null /dev/zero

FILES
=====

| */dev/null*
| */dev/zero*

NOTES
=====

If these devices are not writable and readable for all users, many
programs will act strangely.

Since Linux 2.6.31, reads from */dev/zero* are interruptible by signals.
(This change was made to help with bad latencies for large reads from
*/dev/zero*.)

SEE ALSO
========

**chown**\ (1), **mknod**\ (1), **full**\ (4)
