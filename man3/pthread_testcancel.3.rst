NAME
====

pthread_testcancel - request delivery of any pending cancellation
request

SYNOPSIS
========

::

   #include <pthread.h>

   void pthread_testcancel(void);

   Compile and link with -pthread.

DESCRIPTION
===========

Calling **pthread_testcancel**\ () creates a cancellation point within
the calling thread, so that a thread that is otherwise executing code
that contains no cancellation points will respond to a cancellation
request.

If cancelability is disabled (using **pthread_setcancelstate**\ (3)), or
no cancellation request is pending, then a call to
**pthread_testcancel**\ () has no effect.

RETURN VALUE
============

This function does not return a value. If the calling thread is canceled
as a consequence of a call to this function, then the function does not
return.

ERRORS
======

This function always succeeds.

ATTRIBUTES
==========

For an explanation of the terms used in this section, see
**attributes**\ (7).

========================== ============= =======
Interface                  Attribute     Value
**pthread_testcancel**\ () Thread safety MT-Safe
========================== ============= =======

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008.

EXAMPLES
========

See **pthread_cleanup_push**\ (3).

SEE ALSO
========

**pthread_cancel**\ (3), **pthread_cleanup_push**\ (3),
**pthread_setcancelstate**\ (3), **pthreads**\ (7)
