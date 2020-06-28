NAME
====

hosts - static table lookup for hostnames

SYNOPSIS
========

**/etc/hosts**

DESCRIPTION
===========

This manual page describes the format of the */etc/hosts* file. This
file is a simple text file that associates IP addresses with hostnames,
one line per IP address. For each host a single line should be present
with the following information:

   IP_address canonical_hostname [aliases...]

Fields of the entry are separated by any number of blanks and/or tab
characters. Text from a "#" character until the end of the line is a
comment, and is ignored. Host names may contain only alphanumeric
characters, minus signs ("-"), and periods ("."). They must begin with
an alphabetic character and end with an alphanumeric character. Optional
aliases provide for name changes, alternate spellings, shorter
hostnames, or generic hostnames (for example, *localhost*).

The Berkeley Internet Name Domain (BIND) Server implements the Internet
name server for UNIX systems. It augments or replaces the */etc/hosts*
file or hostname lookup, and frees a host from relying on */etc/hosts*
being up to date and complete.

In modern systems, even though the host table has been superseded by
DNS, it is still widely used for:

**bootstrapping**
   Most systems have a small host table containing the name and address
   information for important hosts on the local network. This is useful
   when DNS is not running, for example during system bootup.

**NIS**
   Sites that use NIS use the host table as input to the NIS host
   database. Even though NIS can be used with DNS, most NIS sites still
   use the host table with an entry for all local hosts as a backup.

**isolated nodes**
   Very small sites that are isolated from the network use the host
   table instead of DNS. If the local information rarely changes, and
   the network is not connected to the Internet, DNS offers little
   advantage.

FILES
=====

*/etc/hosts*

NOTES
=====

Modifications to this file normally take effect immediately, except in
cases where the file is cached by applications.

Historical notes
----------------

RFC 952 gave the original format for the host table, though it has since
changed.

Before the advent of DNS, the host table was the only way of resolving
hostnames on the fledgling Internet. Indeed, this file could be created
from the official host data base maintained at the Network Information
Control Center (NIC), though local changes were often required to bring
it up to date regarding unofficial aliases and/or unknown hosts. The NIC
no longer maintains the hosts.txt files, though looking around at the
time of writing (circa 2000), there are historical hosts.txt files on
the WWW. I just found three, from 92, 94, and 95.

EXAMPLES
========

::

   # The following lines are desirable for IPv4 capable hosts
   127.0.0.1       localhost

   # 127.0.1.1 is often used for the FQDN of the machine
   127.0.1.1       thishost.mydomain.org  thishost
   192.168.1.10    foo.mydomain.org       foo
   192.168.1.13    bar.mydomain.org       bar
   146.82.138.7    master.debian.org      master
   209.237.226.90  www.opensource.org

   # The following lines are desirable for IPv6 capable hosts
   ::1             localhost ip6-localhost ip6-loopback
   ff02::1         ip6-allnodes
   ff02::2         ip6-allrouters

SEE ALSO
========

**hostname**\ (1), **resolver**\ (3), **host.conf**\ (5),
**resolv.conf**\ (5), **resolver**\ (5), **hostname**\ (7),
**named**\ (8)

Internet RFC 952
