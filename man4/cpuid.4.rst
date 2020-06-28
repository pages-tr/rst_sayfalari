NAME
====

cpuid - x86 CPUID access device

DESCRIPTION
===========

CPUID provides an interface for querying information about the x86 CPU.

This device is accessed by **lseek**\ (2) or **pread**\ (2) to the
appropriate CPUID level and reading in chunks of 16 bytes. A larger read
size means multiple reads of consecutive levels.

The lower 32 bits of the file position is used as the incoming *%eax*,
and the upper 32 bits of the file position as the incoming *%ecx*, the
latter is intended for "counting" *eax* levels like *eax=4*.

This driver uses */dev/cpu/CPUNUM/cpuid*, where *CPUNUM* is the minor
number, and on an SMP box will direct the access to CPU *CPUNUM* as
listed in */proc/cpuinfo*.

This file is protected so that it can be read only by the user *root*,
or members of the group *root*.

NOTES
=====

The CPUID instruction can be directly executed by a program using inline
assembler. However this device allows convenient access to all CPUs
without changing process affinity.

Most of the information in *cpuid* is reported by the kernel in cooked
form either in */proc/cpuinfo* or through subdirectories in
*/sys/devices/system/cpu*. Direct CPUID access through this device
should only be used in exceptional cases.

The *cpuid* driver is not auto-loaded. On modular kernels you might need
to use the following command to load it explicitly before use:

::

   $ modprobe cpuid

There is no support for CPUID functions that require additional input
registers.

Very old x86 CPUs don't support CPUID.

SEE ALSO
========

**cpuid**\ (1)

Intel Corporation, Intel 64 and IA-32 Architectures Software Developer's
Manual Volume 2A: Instruction Set Reference, A-M, 3-180 CPUID reference.

Intel Corporation, Intel Processor Identification and the CPUID
Instruction, Application note 485.
