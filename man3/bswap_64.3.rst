NAME
====

bswap_16, bswap_32, bswap_64 - reverse order of bytes

SYNOPSIS
========

::

   #include <byteswap.h>

   bswap_16(x);
   bswap_32(x);
   bswap_64(x);

DESCRIPTION
===========

These macros return a value in which the order of the bytes in their 2-,
4-, or 8-byte arguments is reversed.

RETURN VALUE
============

These macros return the value of their argument with the bytes reversed.

ERRORS
======

These macros always succeed.

CONFORMING TO
=============

These macros are GNU extensions.

EXAMPLES
========

The program below swaps the bytes of the 8-byte integer supplied as its
command-line argument. The following shell session demonstrates the use
of the program:

::

   $ ./a.out 0x0123456789abcdef
   0x123456789abcdef ==> 0xefcdab8967452301

Program source
--------------

::

   #include <stdio.h>
   #include <stdint.h>
   #include <stdlib.h>
   #include <inttypes.h>
   #include <byteswap.h>

   int
   main(int argc, char *argv[])
   {
       uint64_t x;

       if (argc != 2) {
           fprintf(stderr, "Usage: %s <num>\n", argv[0]);
           exit(EXIT_FAILURE);
       }

       x = strtoul(argv[1], NULL, 0);
       printf("0x%" PRIx64 " ==> 0x%" PRIx64 "\n", x, bswap_64(x));

       exit(EXIT_SUCCESS);
   }

SEE ALSO
========

**byteorder**\ (3), **endian**\ (3)
