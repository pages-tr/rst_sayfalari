NAME
====

hostname - hostname resolution description

DESCRIPTION
===========

Hostnames are domains, where a domain is a hierarchical, dot-separated
list of subdomains; for example, the machine "monet", in the "example"
subdomain of the "com" domain would be represented as
"monet.example.com".

Each element of the hostname must be from 1 to 63 characters long and
the entire hostname, including the dots, can be at most 253 characters
long. Valid characters for hostnames are **ASCII**\ (7) letters from *a*
to *z*, the digits from *0* to *9*, and the hyphen (-). A hostname may
not start with a hyphen.

Hostnames are often used with network client and server programs, which
must generally translate the name to an address for use. (This task is
generally performed by either **getaddrinfo**\ (3) or the obsolete
**gethostbyname**\ (3).)

Hostnames are resolved by the NSS framework in glibc according to the
**hosts** configuration in **nsswitch.conf**. The DNS-based name
resolver (in the **dns** NSS service module) resolves them in the
following fashion.

If the name consists of a single component, that is, contains no dot,
and if the environment variable **HOSTALIASES** is set to the name of a
file, that file is searched for any string matching the input hostname.
The file should consist of lines made up of two white-space separated
strings, the first of which is the hostname alias, and the second of
which is the complete hostname to be substituted for that alias. If a
case-insensitive match is found between the hostname to be resolved and
the first field of a line in the file, the substituted name is looked up
with no further processing.

If the input name ends with a trailing dot, the trailing dot is removed,
and the remaining name is looked up with no further processing.

If the input name does not end with a trailing dot, it is looked up by
searching through a list of domains until a match is found. The default
search list includes first the local domain, then its parent domains
with at least 2 name components (longest first). For example, in the
domain cs.example.com, the name lithium.cchem will be checked first as
lithium.cchem.cs.example and then as lithium.cchem.example.com.
lithium.cchem.com will not be tried, as there is only one component
remaining from the local domain. The search path can be changed from the
default by a system-wide configuration file (see **resolver**\ (5)).

SEE ALSO
========

**getaddrinfo**\ (3), **gethostbyname**\ (3), **nsswitch.conf**\ (5),
**resolver**\ (5), **mailaddr**\ (7), **named**\ (8)

`IETF RFC 1123 <http://www.ietf.org/rfc/rfc1123.txt>`__

`IETF RFC 1178 <http://www.ietf.org/rfc/rfc1178.txt>`__
