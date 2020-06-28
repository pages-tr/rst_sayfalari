NAME
====

tzselect - select a timezone

SYNOPSIS
========

**tzselect**

DESCRIPTION
===========

The **tzselect** program asks the user for information about the current
location, and outputs the resulting timezone description to standard
output. The output is suitable as a value for the **TZ** environment
variable.

All interaction with the user is done via standard input and standard
error.

EXIT STATUS
===========

The exit status is zero if a timezone was successfully obtained from the
user, and is nonzero otherwise.

ENVIRONMENT
===========

**AWK**
   Name of a POSIX-compliant *awk* program (default: **awk**).

**TZDIR**
   Name of the directory containing timezone data files (default:
   */usr/share/zoneinfo*).

FILES
=====

**TZDIR**\ */iso3166.tab*
   Table of ISO 3166 2-letter country codes and country names.

**TZDIR**\ */zone.tab*
   Table of country codes, latitude and longitude, TZ values, and
   descriptive comments.

**TZDIR**\ */TZ*
   Timezone data file for timezone *TZ*.

SEE ALSO
========

**tzfile**\ (5), **zdump**\ (8), **zic**\ (8)
