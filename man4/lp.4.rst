NAME
====

lp - line printer devices

SYNOPSIS
========

**#include <linux/lp.h>**

CONFIGURATION
=============

**lp**\ [0–2] are character devices for the parallel line printers; they
have major number 6 and minor number 0–2. The minor numbers correspond
to the printer port base addresses 0x03bc, 0x0378, and 0x0278. Usually
they have mode 220 and are owned by user *root* and group *lp*. You can
use printer ports either with polling or with interrupts. Interrupts are
recommended when high traffic is expected, for example, for laser
printers. For typical dot matrix printers, polling will usually be
enough. The default is polling.

DESCRIPTION
===========

The following **ioctl**\ (2) calls are supported:

-  Sets the amount of time that the driver sleeps before rechecking the
   printer when the printer's buffer appears to be filled to *arg*. If
   you have a fast printer, decrease this number; if you have a slow
   printer, then increase it. This is in hundredths of a second, the
   default 2 being 0.02 seconds. It influences only the polling driver.

-  Sets the maximum number of busy-wait iterations which the polling
   driver does while waiting for the printer to get ready for receiving
   a character to *arg*. If printing is too slow, increase this number;
   if the system gets too slow, decrease this number. The default is
   1000. It influences only the polling driver.

-  If *arg* is 0, the printer driver will retry on errors, otherwise it
   will abort. The default is 0.

-  If *arg* is 0, **open**\ (2) will be aborted on error, otherwise
   error will be ignored. The default is to ignore it.

-  If *arg* is 0, then the out-of-paper, offline, and error signals are
   required to be false on all writes, otherwise they are ignored. The
   default is to ignore them.

-  Sets the number of busy waiting iterations to wait before strobing
   the printer to accept a just-written character, and the number of
   iterations to wait before turning the strobe off again, to *arg*. The
   specification says this time should be 0.5 microseconds, but
   experience has shown the delay caused by the code is already enough.
   For that reason, the default value is 0. This is used for both the
   polling and the interrupt driver.

-  This **ioctl**\ (2) requires superuser privileges. It takes an *int*
   containing the new IRQ as argument. As a side effect, the printer
   will be reset. When *arg* is 0, the polling driver will be used,
   which is also default.

-  Stores the currently used IRQ in *arg*.

-  Stores the value of the status port in *arg*. The bits have the
   following meaning:

========== =========================================
LP_PBUSY   inverted busy input, active high
LP_PACK    unchanged acknowledge input, active low
LP_POUTPA  unchanged out-of-paper input, active high
LP_PSELECD unchanged selected input, active high
LP_PERRORP unchanged error input, active low
========== =========================================

..

   Refer to your printer manual for the meaning of the signals. Note
   that undocumented bits may also be set, depending on your printer.

-  Resets the printer. No argument is used.

FILES
=====

*/dev/lp\**

SEE ALSO
========

**chmod**\ (1), **chown**\ (1), **mknod**\ (1), **lpcntl**\ (8),
**tunelp**\ (8)
