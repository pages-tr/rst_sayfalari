NAME
====

veth - Virtual Ethernet Device

DESCRIPTION
===========

The **veth** devices are virtual Ethernet devices. They can act as
tunnels between network namespaces to create a bridge to a physical
network device in another namespace, but can also be used as standalone
network devices.

**veth** devices are always created in interconnected pairs. A pair can
be created using the command:

::

   # ip link add <p1-name> type veth peer name <p2-name>

In the above, *p1-name* and *p2-name* are the names assigned to the two
connected end points.

Packets transmitted on one device in the pair are immediately received
on the other device. When either devices is down the link state of the
pair is down.

**veth** device pairs are useful for combining the network facilities of
the kernel together in interesting ways. A particularly interesting use
case is to place one end of a **veth** pair in one network namespace and
the other end in another network namespace, thus allowing communication
between network namespaces. To do this, one can provide the **netns**
parameter when creating the interfaces:

::

   # ip link add <p1-name> netns <p1-ns> type veth peer <p2-name> netns <p2-ns>

or, for an existing **veth** pair, move one side to the other namespace:

::

   # ip link set <p2-name> netns <p2-ns>

**ethtool**\ (8) can be used to find the peer of a **veth** network
interface, using commands something like:

::

   # ip link add ve_A type veth peer name ve_B   # Create veth pair
   # ethtool -S ve_A         # Discover interface index of peer
   NIC statistics:
        peer_ifindex: 16
   # ip link | grep '^16:'   # Look up interface
   16: ve_B@ve_A: <BROADCAST,MULTICAST,M-DOWN> mtu 1500 qdisc ...

SEE ALSO
========

**clone**\ (2), **network_namespaces**\ (7), **ip**\ (8),
**ip-link**\ (8), **ip-netns**\ (8)
