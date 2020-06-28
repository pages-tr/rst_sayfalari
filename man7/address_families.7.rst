NAME
====

address_families - socket address families (domains)

SYNOPSIS
========

| **#include <sys/types.h>** /\* See NOTES \*/
| **#include <sys/socket.h>**

**int socket(int**\ *domain*\ **, int**\ *type*\ **,
int**\ *protocol*\ **);**

DESCRIPTION
===========

The *domain* argument of the **socket**\ (2) specifies a communication
domain; this selects the protocol family which will be used for
communication. These families are defined in *<sys/socket.h>*. The
formats currently understood by the Linux kernel include:

**AF_UNIX**, **AF_LOCAL**
   Local communication For further information, see **unix**\ (7).

**AF_INET**
   IPv4 Internet protocols. For further information, see **ip**\ (7).

**AF_AX25**
   Amateur radio AX.25 protocol. For further information, see
   **ax25**\ (4).

**AF_IPX**
   IPX - Novell protocols.

**AF_APPLETALK**
   AppleTalk For further information, see **ddp**\ (7).

**AF_NETROM**
   AX.25 packet layer protocol. For further information, see
   **netrom**\ (4),

*The Packet Radio Protocols and Linux*

and the *AX.25*, *NET/ROM*, and *ROSE network programming* chapters of
the

*Linux Amateur Radio AX.25 HOWTO*

**AF_BRIDGE**
   Can't be used for creating sockets; mostly used for bridge links in
   **rtnetlink**\ (7) protocol commands.

**AF_ATMPVC**
   Access to raw ATM Permanent Virtual Circuits (PVCs). For further
   information, see the

*ATM on Linux HOWTO*

**AF_X25**
   ITU-T X.25 / ISO-8208 protocol. For further information, see
   **x25**\ (7).

**AF_INET6**
   IPv6 Internet protocols. For further information, see **ipv6**\ (7).

**AF_ROSE**
   RATS (Radio Amateur Telecommunications Society) Open Systems
   environment (ROSE) AX.25 packet layer protocol. For further
   information, see the resources listed for **AF_NETROM**.

**AF_DECnet**
   DECet protocol sockets. See *Documentation/networking/decnet.txt* in
   the Linux kernel source tree for details.

**AF_NETBEUI**
   Reserved for "802.2LLC project"; never used.

**AF_SECURITY**
   This was a short-lived (between Linux 2.1.30 and 2.1.99pre2) protocol
   family for firewall upcalls.

**AF_KEY**
   Key management protocol, originally developed for usage with IPsec
   (since Linux 2.1.38). This has no relation to **keyctl**\ (2) and the
   in-kernel key storage facility. See

RFC 2367 *PF_KEY Key Management API, Version 2*

for details.

**AF_NETLINK**
   Kernel user interface device For further information, see
   **netlink**\ (7).

**AF_PACKET**
   Low-level packet interface. For further information, see
   **packet**\ (7).

**AF_ECONET**
   Acorn Econet protocol (removed in Linux 3.5). See the `Econet
   documentation <http://www.8bs.com/othrdnld/manuals/econet.shtml>`__
   for details.

**AF_ATMSVC**
   Access to ATM Switched Virtual Circuits (SVCs) See the

*ATM on Linux HOWTO*

for details.

**AF_RDS**
   Reliable Datagram Sockets (RDS) protocol (since Linux 2.6.30). RDS
   over RDMA has no relation to **AF_SMC** or **AF_XDP**. For further
   information see **rds**\ (7), **rds-rdma**\ (7), and
   *Documentation/networking/rds.txt* in the Linux kernel source tree.

**AF_IRDA**
   Socket interface over IrDA (moved to staging in Linux 4.14, removed
   in Linux 4.17). For further information see **irda**\ (7).

**AF_PPPOX**
   Generic PPP transport layer, for setting up L2 tunnels (L2TP and
   PPPoE). See *Documentation/networking/l2tp.txt* in the Linux kernel
   source tree for details.

**AF_WANPIPE**
   Legacy protocol for wide area network (WAN) connectivity that was
   used by Sangoma WAN cards (called "WANPIPE"); removed in Linux
   2.6.21.

**AF_LLC**
   Logical link control (IEEE 802.2 LLC) protocol, upper part of data
   link layer of ISO/OSI networking protocol stack (since Linux 2.4);
   has no relation to **AF_PACKET**. See chapter *13.5.3. Logical Link
   Control* in *Understanding Linux Kernel Internals* (O'Reilly Media,
   2006) and *IEEE Standards for Local Area Networks: Logical Link
   Control* (The Institute of Electronics and Electronics Engineers,
   Inc., New York, New York, 1985) for details. See also `some
   historical notes <https://wiki.linuxfoundation.org/networking/llc>`__
   regarding its development.

**AF_IB**
   InfiniBand native addressing (since Linux 3.11).

**AF_MPLS**
   Multiprotocol Label Switching (since Linux 4.1); mostly used for
   configuring MPLS routing via **netlink**\ (7), as it doesn't expose
   ability to create sockets to user space.

**AF_CAN**
   Controller Area Network automotive bus protocol (since Linux 2.6.25).
   See *Documentation/networking/can.rst* in the Linux kernel source
   tree for details.

**AF_TIPC**
   TIPC, "cluster domain sockets" protocol (since Linux 2.6.16). See

*TIPC Programmer's Guide*

and the `protocol description <http://tipc.io/protocol.html>`__ for
details.

**AF_BLUETOOTH**
   Bluetooth low-level socket protocol (since Linux 3.11). See

*Bluetooth Management API overview*

and

*An Introduction to Bluetooth Programming* by Albert Huang

for details.

**AF_IUCV**
   IUCV (inter-user communication vehicle) z/VM protocol for
   hypervisor-guest interaction (since Linux 2.6.21); has no relation to
   **AF_VSOCK** and/or **AF_SMC** See

*IUCV protocol overview*

for details.

**AF_RXRPC**
   Rx, Andrew File System remote procedure call protocol (since Linux
   2.6.22). See *Documentation/networking/rxrpc.txt* in the Linux kernel
   source tree for details.

**AF_ISDN**
   New "modular ISDN" driver interface protocol (since Linux 2.6.27).
   See the `mISDN wiki <http://www.misdn.eu/wiki/Main_Page/>`__ for
   details.

**AF_PHONET**
   Nokia cellular modem IPC/RPC interface (since Linux 2.6.31). See
   *Documentation/networking/phonet.txt* in the Linux kernel source tree
   for details.

**AF_IEEE802154**
   IEEE 802.15.4 WPAN (wireless personal area network) raw packet
   protocol (since Linux 2.6.31). See
   *Documentation/networking/ieee802154.txt* in the Linux kernel source
   tree for details.

**AF_CAIF**
   Ericsson's Communication CPU to Application CPU interface (CAIF)
   protocol (since Linux 2.6.36). See
   *Documentation/networking/caif/Linux-CAIF.txt* in the Linux kernel
   source tree for details.

**AF_ALG**
   Interface to kernel crypto API (since Linux 2.6.38). See
   *Documentation/crypto/userspace-if.rst* in the Linux kernel source
   tree for details.

**AF_VSOCK**
   VMWare VSockets protocol for hypervisor-guest interaction (since
   Linux 3.9); has no relation to **AF_IUCV** and **AF_SMC**. For
   further information, see **vsock**\ (7).

**AF_KCM**
   KCM (kernel connection multiplexor) interface (since Linux 4.6). See
   *Documentation/networking/kcm.txt* in the Linux kernel source tree
   for details.

**AF_QIPCRTR**
   Qualcomm IPC router interface protocol (since Linux 4.7).

**AF_SMC**
   SMC-R (shared memory communications over RDMA) protocol (since Linux
   4.11), and SMC-D (shared memory communications, direct memory access)
   protocol for intra-node z/VM quest interaction (since Linux 4.19);
   has no relation to **AF_RDS**, **AF_IUCV** or **AF_VSOCK**. See

RFC 7609 *IBM's Shared Memory Communications over RDMA (SMC-R) Protocol*

for details regarding SMC-R. See

*SMC-D Reference Information*

for details regarding SMC-D.

**AF_XDP**
   XDP (express data path) interface (since Linux 4.18). See
   *Documentation/networking/af_xdp.rst* in the Linux kernel source tree
   for details.

SEE ALSO
========

**socket**\ (2), **socket**\ (7)
