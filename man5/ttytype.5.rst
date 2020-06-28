NAME
====

ttytype - terminal device to default terminal type mapping

DESCRIPTION
===========

The */etc/ttytype* file associates **termcap**\ (5)/**terminfo**\ (5)
terminal type names with tty lines. Each line consists of a terminal
type, followed by whitespace, followed by a tty name (a device name
without the */dev/*) prefix.

This association is used by the program **tset**\ (1) to set the
environment variable **TERM** to the default terminal name for the
user's current tty.

This facility was designed for a traditional time-sharing environment
featuring character-cell terminals hardwired to a UNIX minicomputer. It
is little used on modern workstation and personal UNIX systems.

FILES
=====

*/etc/ttytype*
   the tty definitions file.

EXAMPLES
========

A typical */etc/ttytype* is:

::

   con80x25 tty1
   vt320 ttys0

SEE ALSO
========

**termcap**\ (5), **terminfo**\ (5), **agetty**\ (8), **mingetty**\ (8)
