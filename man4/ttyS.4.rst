NAME
====

ttyS - serial terminal lines

DESCRIPTION
===========

**ttyS[0-3]** are character devices for the serial terminal lines.

They are typically created by:

::

   mknod -m 660 /dev/ttyS0 c 4 64 # base address 0x3f8
   mknod -m 660 /dev/ttyS1 c 4 65 # base address 0x2f8
   mknod -m 660 /dev/ttyS2 c 4 66 # base address 0x3e8
   mknod -m 660 /dev/ttyS3 c 4 67 # base address 0x2e8
   chown root:tty /dev/ttyS[0-3]

FILES
=====

*/dev/ttyS[0-3]*

SEE ALSO
========

**chown**\ (1), **mknod**\ (1), **tty**\ (4), **agetty**\ (8),
**mingetty**\ (8), **setserial**\ (8)
