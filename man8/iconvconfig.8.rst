NAME
====

iconvconfig - create iconv module configuration cache

SYNOPSIS
========

**iconvconfig** [*options*] [*directory*]...

DESCRIPTION
===========

The **iconv**\ (3) function internally uses *gconv* modules to convert
to and from a character set. A configuration file is used to determine
the needed modules for a conversion. Loading and parsing such a
configuration file would slow down programs that use **iconv**\ (3), so
a caching mechanism is employed.

The **iconvconfig** program reads iconv module configuration files and
writes a fast-loading gconv module configuration cache file.

In addition to the system provided gconv modules, the user can specify
custom gconv module directories with the environment variable
**GCONV_PATH**. However, iconv module configuration caching is used only
when the environment variable **GCONV_PATH** is not set.

OPTIONS
=======

**--nostdlib**
   Do not search the system default gconv directory, only the
   directories provided on the command line.

**-o**\ *outputfile*\ **, --output=**\ *outputfile*
   Use *outputfile* for output instead of the system default cache
   location.

**--prefix=**\ *pathname*
   Set the prefix to be prepended to the system pathnames. See FILES,
   below. By default, the prefix is empty. Setting the prefix to *foo*,
   the gconv module configuration would be read from
   *foo/usr/lib/gconv/gconv-modules* and the cache would be written to
   *foo/usr/lib/gconv/gconv-modules.cache*.

**-?**, **--help**
   Print a usage summary and exit.

**--usage**
   Print a short usage summary and exit.

**-V**, **--version**
   Print the version number, license, and disclaimer of warranty for
   **iconv**.

EXIT STATUS
===========

Zero on success, nonzero on errors.

FILES
=====

*/usr/lib/gconv*
   Usual default gconv module path.

*/usr/lib/gconv/gconv-modules*
   Usual system default gconv module configuration file.

*/usr/lib/gconv/gconv-modules.cache*
   Usual system gconv module configuration cache.

SEE ALSO
========

**iconv**\ (1), **iconv**\ (3)
