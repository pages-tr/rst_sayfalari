NAME
====

ldconfig - configure dynamic linker run-time bindings

SYNOPSIS
========

**/sbin/ldconfig** [**-nNvXV**] [**-f** *conf*] [**-C** *cache*] [**-r**
*root*] *directory*...

**/sbin/ldconfig** **-l** [**-v**] *library*...

**/sbin/ldconfig** **-p**

DESCRIPTION
===========

**ldconfig** creates the necessary links and cache to the most recent
shared libraries found in the directories specified on the command line,
in the file */etc/ld.so.conf*, and in the trusted directories, */lib*
and */usr/lib* (on some 64-bit architectures such as x86-64, */lib* and
*/usr/lib* are the trusted directories for 32-bit libraries, while
*/lib64* and */usr/lib64* are used for 64-bit libraries).

The cache is used by the run-time linker, *ld.so* or *ld-linux.so*.
**ldconfig** checks the header and filenames of the libraries it
encounters when determining which versions should have their links
updated.

**ldconfig** will attempt to deduce the type of ELF libraries (i.e.,
libc5 or libc6/glibc) based on what C libraries, if any, the library was
linked against.

Some existing libraries do not contain enough information to allow the
deduction of their type. Therefore, the */etc/ld.so.conf* file format
allows the specification of an expected type. This is used *only* for
those ELF libraries which we can not work out. The format is
"dirname=TYPE", where TYPE can be libc4, libc5, or libc6. (This syntax
also works on the command line.) Spaces are *not* allowed. Also see the
**-p** option. **ldconfig** should normally be run by the superuser as
it may require write permission on some root owned directories and
files.

Note that **ldconfig** will only look at files that are named
*lib*.so\** (for regular shared objects) or *ld-*.so\** (for the dynamic
loader itself). Other files will be ignored. Also, **ldconfig** expects
a certain pattern to how the symlinks are set up, like this example,
where the middle file (**libfoo.so.1** here) is the SONAME for the
library:

::

   libfoo.so -> libfoo.so.1 -> libfoo.so.1.12

Failure to follow this pattern may result in compatibility issues after
an upgrade.

OPTIONS
=======

**-c** *fmt*, **--format=\ fmt**
   (Since glibc 2.2) Cache format to use: *old*, *new*, or *compat*.
   Since glibc 2.32, the default is *new*. Before that, it was *compat*.

**-C**\ *cache*
   Use *cache* instead of */etc/ld.so.cache*.

**-f**\ *conf*
   Use *conf* instead of */etc/ld.so.conf*.

**-i**, **--ignore-aux-cache**
   (Since glibc 2.7) Ignore auxiliary cache file.

**-l**
   (Since glibc 2.2) Library mode. Manually link individual libraries.
   Intended for use by experts only.

**-n**
   Process only the directories specified on the command line. Don't
   process the trusted directories, nor those specified in
   */etc/ld.so.conf*. Implies **-N**.

**-N**
   Don't rebuild the cache. Unless **-X** is also specified, links are
   still updated.

**-p**, **--print-cache**
   Print the lists of directories and candidate libraries stored in the
   current cache.

**-r**\ *root*
   Change to and use *root* as the root directory.

**-v**, **--verbose**
   Verbose mode. Print current version number, the name of each
   directory as it is scanned, and any links that are created. Overrides
   quiet mode.

**-V**, **--version**
   Print program version.

**-X**
   Don't update links. Unless **-N** is also specified, the cache is
   still rebuilt.

FILES
=====

*/lib/ld.so*
   Run-time linker/loader.

*/etc/ld.so.conf*
   File containing a list of directories, one per line, in which to
   search for libraries.

*/etc/ld.so.cache*
   File containing an ordered list of libraries found in the directories
   specified in */etc/ld.so.conf*, as well as those found in the trusted
   directories.

SEE ALSO
========

**ldd**\ (1), **ld.so**\ (8)
