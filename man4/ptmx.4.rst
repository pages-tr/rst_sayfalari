NAME
====

ptmx, pts - pseudoterminal master and slave

DESCRIPTION
===========

The file */dev/ptmx* is a character file with major number 5 and minor
number 2, usually with mode 0666 and ownership root:root. It is used to
create a pseudoterminal master and slave pair.

When a process opens */dev/ptmx*, it gets a file descriptor for a
pseudoterminal master (PTM), and a pseudoterminal slave (PTS) device is
created in the */dev/pts* directory. Each file descriptor obtained by
opening */dev/ptmx* is an independent PTM with its own associated PTS,
whose path can be found by passing the file descriptor to
**ptsname**\ (3).

Before opening the pseudoterminal slave, you must pass the master's file
descriptor to **grantpt**\ (3) and **unlockpt**\ (3).

Once both the pseudoterminal master and slave are open, the slave
provides processes with an interface that is identical to that of a real
terminal.

Data written to the slave is presented on the master file descriptor as
input. Data written to the master is presented to the slave as input.

In practice, pseudoterminals are used for implementing terminal
emulators such as **xterm**\ (1), in which data read from the
pseudoterminal master is interpreted by the application in the same way
a real terminal would interpret the data, and for implementing
remote-login programs such as **sshd**\ (8), in which data read from the
pseudoterminal master is sent across the network to a client program
that is connected to a terminal or terminal emulator.

Pseudoterminals can also be used to send input to programs that normally
refuse to read input from pipes (such as **su**\ (1), and
**passwd**\ (1)).

FILES
=====

*/dev/ptmx*, */dev/pts/\**

NOTES
=====

The Linux support for the above (known as UNIX 98 pseudoterminal naming)
is done using the *devpts* filesystem, that should be mounted on
*/dev/pts*.

Before this UNIX 98 scheme, master pseudoterminals were called
*/dev/ptyp0*, ... and slave pseudoterminals */dev/ttyp0*, ... and one
needed lots of preallocated device nodes.

SEE ALSO
========

**getpt**\ (3), **grantpt**\ (3), **ptsname**\ (3), **unlockpt**\ (3),
**pty**\ (7)
