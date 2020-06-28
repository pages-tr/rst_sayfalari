NAME
====

s390_guarded_storage - operations with z/Architecture guarded storage
facility

SYNOPSIS
========

::

   #include <asm/guarded_storage.h>

   int s390_guarded_storage(int command, struct gs_cb *gs_cb);

DESCRIPTION
===========

The **s390_guarded_storage**\ () system call enables the use of the
Guarded Storage Facility (a z/Architecture-specific feature) for
user-space processes.

The guarded storage facility is a hardware feature that allows marking
up to 64 memory regions (as of z14) as guarded; reading a pointer with a
newly introduced "Load Guarded" (LGG) or "Load Logical and Shift
Guarded" (LLGFSG) instructions will cause a range check on the loaded
value and invoke a (previously set up) user-space handler if one of the
guarded regions is affected.

The *command* argument indicates which function to perform. The
following commands are supported:

**GS_ENABLE**
   Enable the guarded storage facility for the calling task. The initial
   content of the guarded storage control block will be all zeros. After
   enablement, user-space code can use the "Load Guarded Storage
   Controls" (LGSC) instruction (or the **load_gs_cb**\ () function
   wrapper provided in the *asm/guarded_storage.h* header) to load an
   arbitrary control block. While a task is enabled, the kernel will
   save and restore the calling content of the guarded storage registers
   on context switch.

**GS_DISABLE**
   Disables the use of the guarded storage facility for the calling
   task. The kernel will cease to save and restore the content of the
   guarded storage registers, the task-specific content of these
   registers is lost.

**GS_SET_BC_CB**
   Set a broadcast guarded storage control block to the one provided in
   the *gs_cb* argument. This is called per thread and associates a
   specific guarded storage control block with the calling task. This
   control block will be used in the broadcast command **GS_BROADCAST**.

**GS_CLEAR_BC_CB**
   Clears the broadcast guarded storage control block. The guarded
   storage control block will no longer have the association established
   by the **GS_SET_BC_CB** command.

**GS_BROADCAST**
   Sends a broadcast to all thread siblings of the calling task. Every
   sibling that has established a broadcast guarded storage control
   block will load this control block and will be enabled for guarded
   storage. The broadcast guarded storage control block is consumed; a
   second broadcast without a refresh of the stored control block with
   **GS_SET_BC_CB** will not have any effect.

The *gs_cb* argument specifies the address of a guarded storage control
block structure and is currently used only by the **GS_SET_BC_CB**
command; all other aforementioned commands ignore this argument.

RETURN VALUE
============

On success, the return value of **s390_guarded_storage**\ () is 0.

On error, -1 is returned, and *errno* is set appropriately.

ERRORS
======

**EFAULT**
   *command* was **GS_SET_BC_CB** and the copying of the guarded storage
   control block structure pointed by the *gs_cb* argument has failed.

**EINVAL**
   The value provided in the *command* argument was not valid.

**ENOMEM**
   *command* was one of **GS_ENABLE** or **GS_SET_BC_CB**, and the
   allocation of a new guarded storage control block has failed.

**EOPNOTSUPP**
   The guarded storage facility is not supported by the hardware.

VERSIONS
========

This system call is available since Linux 4.12.

CONFORMING TO
=============

This Linux-specific system call is available only on the s390
architecture.

The guarded storage facility is available beginning with System z14.

NOTES
=====

Glibc does not provide a wrapper for this system call, use
**syscall**\ (2) to call it.

The description of the guarded storage facility along with related
instructions and Guarded Storage Control Block and Guarded Storage Event
Parameter List structure layouts is available in "z/Architecture
Principles of Operations" beginning from the twelfth edition.

The *gs_cb* structure has a field *gsepla* (Guarded Storage Event
Parameter List Address), which is a user-space pointer to a Guarded
Storage Event Parameter List structure (that contains the address of the
aforementioned event handler in the *gseha* field), and its layout is
available as a **gs_epl** structure type definition in the
*asm/guarded_storage.h* header.

SEE ALSO
========

**syscall**\ (2)
