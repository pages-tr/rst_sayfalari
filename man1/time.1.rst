NAME
====

time - time a simple command or give resource usage

SYNOPSIS
========

**time [**\ *options*\ **]**\ *command*\ **[**\ *arguments...*\ **]**

DESCRIPTION
===========

The **time** command runs the specified program *command* with the given
arguments. When *command* finishes, **time** writes a message to
standard error giving timing statistics about this program run. These
statistics consist of (i) the elapsed real time between invocation and
termination, (ii) the user CPU time (the sum of the *tms_utime* and
*tms_cutime* values in a *struct tms* as returned by **times**\ (2)),
and (iii) the system CPU time (the sum of the *tms_stime* and
*tms_cstime* values in a *struct tms* as returned by **times**\ (2)).

Note: some shells (e.g., **bash**\ (1)) have a built-in **time** command
that provides similar information on the usage of time and possibly
other resources. To access the real command, you may need to specify its
pathname (something like */usr/bin/time*).

OPTIONS
=======

**-p**
   When in the POSIX locale, use the precise traditional format

   ::

      "real %f\nuser %f\nsys %f\n"

   (with numbers in seconds) where the number of decimals in the output
   for %f is unspecified but is sufficient to express the clock tick
   accuracy, and at least one.

EXIT STATUS
===========

If *command* was invoked, the exit status is that of *command*.
Otherwise, it is 127 if *command* could not be found, 126 if it could be
found but could not be invoked, and some other nonzero value (1–125) if
something else went wrong.

ENVIRONMENT
===========

The variables **LANG**, **LC_ALL**, **LC_CTYPE**, **LC_MESSAGES**,
**LC_NUMERIC**, and **NLSPATH** are used for the text and formatting of
the output. **PATH** is used to search for *command*. The remaining ones
for the text and formatting of the output.

GNU VERSION
===========

Below a description of the GNU 1.7 version of **time**. Disregarding the
name of the utility, GNU makes it output lots of useful information, not
only about time used, but also on other resources like memory, I/O and
IPC calls (where available). The output is formatted using a format
string that can be specified using the *-f* option or the **TIME**
environment variable.

The default format string is:

::

   %Uuser %Ssystem %Eelapsed %PCPU (%Xtext+%Ddata %Mmax)k
   %Iinputs+%Ooutputs (%Fmajor+%Rminor)pagefaults %Wswaps

When the *-p* option is given, the (portable) output format is used:

::

   real %e
   user %U
   sys %S

The format string
-----------------

The format is interpreted in the usual printf-like way. Ordinary
characters are directly copied, tab, newline and backslash are escaped
using \\t, \\n and \\\, a percent sign is represented by %%, and
otherwise % indicates a conversion. The program **time** will always add
a trailing newline itself. The conversions follow. All of those used by
**tcsh**\ (1) are supported.

**Time**

**%E**
   Elapsed real time (in [hours:]minutes:seconds).

**%e**
   (Not in **tcsh**\ (1).) Elapsed real time (in seconds).

**%S**
   Total number of CPU-seconds that the process spent in kernel mode.

**%U**
   Total number of CPU-seconds that the process spent in user mode.

**%P**
   Percentage of the CPU that this job got, computed as (%U + %S) / %E.

**Memory**

**%M**
   Maximum resident set size of the process during its lifetime, in
   Kbytes.

**%t**
   (Not in **tcsh**\ (1).) Average resident set size of the process, in
   Kbytes.

**%K**
   Average total (data+stack+text) memory use of the process, in Kbytes.

**%D**
   Average size of the process's unshared data area, in Kbytes.

**%p**
   (Not in **tcsh**\ (1).) Average size of the process's unshared stack
   space, in Kbytes.

**%X**
   Average size of the process's shared text space, in Kbytes.

**%Z**
   (Not in **tcsh**\ (1).) System's page size, in bytes. This is a
   per-system constant, but varies between systems.

**%F**
   Number of major page faults that occurred while the process was
   running. These are faults where the page has to be read in from disk.

**%R**
   Number of minor, or recoverable, page faults. These are faults for
   pages that are not valid but which have not yet been claimed by other
   virtual pages. Thus the data in the page is still valid but the
   system tables must be updated.

**%W**
   Number of times the process was swapped out of main memory.

**%c**
   Number of times the process was context-switched involuntarily
   (because the time slice expired).

**%w**
   Number of waits: times that the program was context-switched
   voluntarily, for instance while waiting for an I/O operation to
   complete.

**I/O**

**%I**
   Number of filesystem inputs by the process.

**%O**
   Number of filesystem outputs by the process.

**%r**
   Number of socket messages received by the process.

**%s**
   Number of socket messages sent by the process.

**%k**
   Number of signals delivered to the process.

**%C**
   (Not in **tcsh**\ (1).) Name and command-line arguments of the
   command being timed.

**%x**
   (Not in **tcsh**\ (1).) Exit status of the command.

GNU options
-----------

**-f**\ *format*\ **, --format=**\ *format*
   Specify output format, possibly overriding the format specified in
   the environment variable TIME.

**-p, --portability**
   Use the portable output format.

**-o**\ *file*\ **, --output=**\ *file*
   Do not send the results to *stderr*, but overwrite the specified
   file.

**-a, --append**
   (Used together with -o.) Do not overwrite but append.

**-v, --verbose**
   Give very verbose output about all the program knows about.

**-q, --quiet**
   Don't report abnormal program termination (where *command* is
   terminated by a signal) or nonzero exit status.

GNU standard options
--------------------

**--help**
   Print a usage message on standard output and exit successfully.

**-V, --version**
   Print version information on standard output, then exit successfully.

**--**
   Terminate option list.

BUGS
====

Not all resources are measured by all versions of UNIX, so some of the
values might be reported as zero. The present selection was mostly
inspired by the data provided by 4.2 or 4.3BSD.

GNU time version 1.7 is not yet localized. Thus, it does not implement
the POSIX requirements.

The environment variable **TIME** was badly chosen. It is not unusual
for systems like **autoconf**\ (1) or **make**\ (1) to use environment
variables with the name of a utility to override the utility to be used.
Uses like MORE or TIME for options to programs (instead of program
pathnames) tend to lead to difficulties.

It seems unfortunate that *-o* overwrites instead of appends. (That is,
the *-a* option should be the default.)

Mail suggestions and bug reports for GNU **time** to *bug-time@gnu.org*.
Please include the version of **time**, which you can get by running

::

   time --version

and the operating system and C compiler you used.

SEE ALSO
========

**bash**\ (1), **tcsh**\ (1), **times**\ (2), **wait3**\ (2)
