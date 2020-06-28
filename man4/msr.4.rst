NAME
====

msr - x86 CPU MSR access device

DESCRIPTION
===========

*/dev/cpu/CPUNUM/msr* provides an interface to read and write the
model-specific registers (MSRs) of an x86 CPU. *CPUNUM* is the number of
the CPU to access as listed in */proc/cpuinfo*.

The register access is done by opening the file and seeking to the MSR
number as offset in the file, and then reading or writing in chunks of 8
bytes. An I/O transfer of more than 8 bytes means multiple reads or
writes of the same register.

This file is protected so that it can be read and written only by the
user *root*, or members of the group *root*.

NOTES
=====

The *msr* driver is not auto-loaded. On modular kernels you might need
to use the following command to load it explicitly before use:

::

   $ modprobe msr

SEE ALSO
========

Intel Corporation Intel 64 and IA-32 Architectures Software Developer's
Manual Volume 3B Appendix B, for an overview of the Intel CPU MSRs.
