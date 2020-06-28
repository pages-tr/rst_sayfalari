NAME
====

pciconfig_read, pciconfig_write, pciconfig_iobase - pci device
information handling

SYNOPSIS
========

::

   #include <pci.h>

   int pciconfig_read(unsigned long bus, unsigned long dfn,
    unsigned long off, unsigned long len, void *buf);
   int pciconfig_write(unsigned long bus, unsigned long dfn,
    unsigned long off, unsigned long len, void *buf);
   int pciconfig_iobase(long which, unsigned long bus,
    unsigned long devfn);

DESCRIPTION
===========

Most of the interaction with PCI devices is already handled by the
kernel PCI layer, and thus these calls should not normally need to be
accessed from user space.

**pciconfig_read**\ ()
   Reads to *buf* from device *dev* at offset *off* value.

**pciconfig_write**\ ()
   Writes from *buf* to device *dev* at offset *off* value.

**pciconfig_iobase**\ ()
   You pass it a bus/devfn pair and get a physical address for either
   the memory offset (for things like prep, this is 0xc0000000), the IO
   base for PIO cycles, or the ISA holes if any.

RETURN VALUE
============

**pciconfig_read**\ ()
   On success, zero is returned. On error, -1 is returned and *errno* is
   set appropriately.

**pciconfig_write**\ ()
   On success, zero is returned. On error, -1 is returned and *errno* is
   set appropriately.

**pciconfig_iobase**\ ()
   Returns information on locations of various I/O regions in physical
   memory according to the *which* value. Values for *which* are:
   **IOBASE_BRIDGE_NUMBER**, **IOBASE_MEMORY**, **IOBASE_IO**,
   **IOBASE_ISA_IO**, **IOBASE_ISA_MEM**.

ERRORS
======

**EINVAL**
   *len* value is invalid. This does not apply to
   **pciconfig_iobase**\ ().

**EIO**
   I/O error.

**ENODEV**
   For **pciconfig_iobase**\ (), "hose" value is NULL. For the other
   calls, could not find a slot.

**ENOSYS**
   The system has not implemented these calls (**CONFIG_PCI** not
   defined).

**EOPNOTSUPP**
   This return value is valid only for **pciconfig_iobase**\ (). It is
   returned if the value for *which* is invalid.

**EPERM**
   User does not have the **CAP_SYS_ADMIN** capability. This does not
   apply to **pciconfig_iobase**\ ().

CONFORMING TO
=============

These calls are Linux-specific, available since Linux 2.0.26/2.1.11.

SEE ALSO
========

**capabilities**\ (7)
