NAME
====

host.conf - resolver configuration file

DESCRIPTION
===========

The file */etc/host.conf* contains configuration information specific to
the resolver library. It should contain one configuration keyword per
line, followed by appropriate configuration information. The following
keywords are recognized:

*trim*
   This keyword may be listed more than once. Each time it should be
   followed by a list of domains, separated by colons (':'), semicolons
   (';') or commas (','), with the leading dot. When set, the resolver
   library will automatically trim the given domain name from the end of
   any hostname resolved via DNS. This is intended for use with local
   hosts and domains. (Related note: *trim* will not affect hostnames
   gathered via NIS or the **hosts**\ (5) file. Care should be taken to
   ensure that the first hostname for each entry in the hosts file is
   fully qualified or unqualified, as appropriate for the local
   installation.)

*multi*
   Valid values are *on* and *off*. If set to *on*, the resolver library
   will return all valid addresses for a host that appears in the
   */etc/hosts* file, instead of only the first. This is *off* by
   default, as it may cause a substantial performance loss at sites with
   large hosts files.

*reorder*
   Valid values are *on* and *off*. If set to *on*, the resolver library
   will attempt to reorder host addresses so that local addresses (i.e.,
   on the same subnet) are listed first when a **gethostbyname**\ (3) is
   performed. Reordering is done for all lookup methods. The default
   value is *off*.

ENVIRONMENT
===========

The following environment variables can be used to allow users to
override the behavior which is configured in */etc/host.conf*:

**RESOLV_HOST_CONF**
   If set, this variable points to a file that should be read instead of
   */etc/host.conf*.

**RESOLV_MULTI**
   Overrides the *multi* command.

**RESOLV_REORDER**
   Overrides the *reorder* command.

**RESOLV_ADD_TRIM_DOMAINS**
   A list of domains, separated by colons (':'), semicolons (';') or
   commas (','), with the leading dot, which will be added to the list
   of domains that should be trimmed.

**RESOLV_OVERRIDE_TRIM_DOMAINS**
   A list of domains, separated by colons (':'), semicolons (';') or
   commas (','), with the leading dot, which will replace the list of
   domains that should be trimmed. Overrides the *trim* command.

FILES
=====

*/etc/host.conf*
   Resolver configuration file

*/etc/resolv.conf*
   Resolver configuration file

*/etc/hosts*
   Local hosts database

NOTES
=====

The following differences exist compared to the original implementation.
A new command *spoof* and a new environment variable
**RESOLV_SPOOF_CHECK** can take arguments like *off*, *nowarn*, and
*warn*. Line comments can appear anywhere and not only at the beginning
of a line.

Historical
----------

The **nsswitch.conf**\ (5) file is the modern way of controlling the
order of host lookups.

In glibc 2.4 and earlier, the following keyword is recognized:

*order*
   This keyword specifies how host lookups are to be performed. It
   should be followed by one or more lookup methods, separated by
   commas. Valid methods are *bind*, *hosts*, and *nis*.

**RESOLV_SERV_ORDER**
   Overrides the *order* command.

Since glibc 2.0.7, and up through glibc 2.24, the following keywords and
environment variable have been recognized but never implemented:

*nospoof*
   Valid values are *on* and *off*. If set to *on*, the resolver library
   will attempt to prevent hostname spoofing to enhance the security of
   **rlogin** and **rsh**. It works as follows: after performing a host
   address lookup, the resolver library will perform a hostname lookup
   for that address. If the two hostnames do not match, the query fails.
   The default value is *off*.

*spoofalert*
   Valid values are *on* and *off*. If this option is set to *on* and
   the *nospoof* option is also set, the resolver library will log a
   warning of the error via the syslog facility. The default value is
   *off*.

*spoof*
   Valid values are *off*, *nowarn*, and *warn*. If this option is set
   to *off*, spoofed addresses are permitted and no warnings will be
   emitted via the syslog facility. If this option is set to *warn*, the
   resolver library will attempt to prevent hostname spoofing to enhance
   the security and log a warning of the error via the syslog facility.
   If this option is set to *nowarn*, the resolver library will attempt
   to prevent hostname spoofing to enhance the security but not emit
   warnings via the syslog facility. Setting this option to anything
   else is equal to setting it to *nowarn*.

**RESOLV_SPOOF_CHECK**
   Overrides the *nospoof*, *spoofalert*, and *spoof* commands in the
   same way as the *spoof* command is parsed. Valid values are *off*,
   *nowarn*, and *warn*.

SEE ALSO
========

**gethostbyname**\ (3), **hosts**\ (5), **nsswitch.conf**\ (5),
**resolv.conf**\ (5), **hostname**\ (7), **named**\ (8)
