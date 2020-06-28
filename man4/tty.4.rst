NAME
====

tty - controlling terminal

DESCRIPTION
===========

The file */dev/tty* is a character file with major number 5 and minor
number 0, usually with mode 0666 and ownership root:tty. It is a synonym
for the controlling terminal of a process, if any.

In addition to the **ioctl**\ (2) requests supported by the device that
**tty** refers to, the **ioctl**\ (2) request **TIOCNOTTY** is
supported.

TIOCNOTTY
---------

Detach the calling process from its controlling terminal.

If the process is the session leader, then **SIGHUP** and **SIGCONT**
signals are sent to the foreground process group and all processes in
the current session lose their controlling tty.

This **ioctl**\ (2) call works only on file descriptors connected to
*/dev/tty*. It is used by daemon processes when they are invoked by a
user at a terminal. The process attempts to open */dev/tty*. If the open
succeeds, it detaches itself from the terminal by using **TIOCNOTTY**,
while if the open fails, it is obviously not attached to a terminal and
does not need to detach itself.

FILES
=====

*/dev/tty*

SEE ALSO
========

**chown**\ (1), **mknod**\ (1), **ioctl**\ (2), **ioctl_console**\ (2),
**ioctl_tty**\ (2), **termios**\ (3), **ttyS**\ (4), **vcs**\ (4),
**pty**\ (7), **agetty**\ (8), **mingetty**\ (8)
