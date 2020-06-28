NAME
====

sd - driver for SCSI disk drives

SYNOPSIS
========

::

   #include <linux/hdreg.h> /* for HDIO_GETGEO */
   #include <linux/fs.h> /* for BLKGETSIZE and BLKRRPART */

CONFIGURATION
=============

The block device name has the following form: **sd**\ *lp,* where *l* is
a letter denoting the physical drive, and *p* is a number denoting the
partition on that physical drive. Often, the partition number, *p*, will
be left off when the device corresponds to the whole drive.

SCSI disks have a major device number of 8, and a minor device number of
the form (16 \* *drive_number*) + *partition_number*, where
*drive_number* is the number of the physical drive in order of
detection, and *partition_number* is as follows:

-  partition 0 is the whole drive

   partitions 1–4 are the DOS "primary" partitions

   partitions 5–8 are the DOS "extended" (or "logical") partitions

For example, */dev/sda* will have major 8, minor 0, and will refer to
all of the first SCSI drive in the system; and */dev/sdb3* will have
major 8, minor 19, and will refer to the third DOS "primary" partition
on the second SCSI drive in the system.

At this time, only block devices are provided. Raw devices have not yet
been implemented.

DESCRIPTION
===========

The following *ioctl*\ s are provided:

**HDIO_GETGEO**
   Returns the BIOS disk parameters in the following structure:

::

   struct hd_geometry {
       unsigned char  heads;
       unsigned char  sectors;
       unsigned short cylinders;
       unsigned long  start;
   };

..

   A pointer to this structure is passed as the **ioctl**\ (2)
   parameter.

   The information returned in the parameter is the disk geometry of the
   drive *as understood by DOS!* This geometry is *not* the physical
   geometry of the drive. It is used when constructing the drive's
   partition table, however, and is needed for convenient operation of
   **fdisk**\ (1), **efdisk**\ (1), and **lilo**\ (1). If the geometry
   information is not available, zero will be returned for all of the
   parameters.

**BLKGETSIZE**
   Returns the device size in sectors. The **ioctl**\ (2) parameter
   should be a pointer to a *long*.

**BLKRRPART**
   Forces a reread of the SCSI disk partition tables. No parameter is
   needed.

   The SCSI **ioctl**\ (2) operations are also supported. If the
   **ioctl**\ (2) parameter is required, and it is NULL, then
   **ioctl**\ (2) fails with the error **EINVAL**.

FILES
=====

*/dev/sd[a-h]*
   the whole device

*/dev/sd[a-h][0-8]*
   individual block partitions
