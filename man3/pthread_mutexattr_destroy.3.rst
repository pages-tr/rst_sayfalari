NAME
====

pthread_mutexattr_init, pthread_mutexattr_destroy - initialize and
destroy a mutex attributes object

SYNOPSIS
========

::

   #include <pthread.h>

   int pthread_mutexattr_init(pthread_mutexattr_t *attr);
   int pthread_mutexattr_destroy(pthread_mutexattr_t *attr);

Compile and link with *-pthread*.

DESCRIPTION
===========

The **pthread_mutexattr_init**\ () function initializes the mutex
attributes object pointed to by *attr* with default values for all
attributes defined by the implementation.

The results of initializing an already initialized mutex attributes
object are undefined.

The **pthread_mutexattr_destroy**\ () function destroys a mutex
attribute object (making it uninitialized). Once a mutex attributes
object has been destroyed, it can be reinitialized with
**pthread_mutexattr_init**\ ().

The results of destroying an uninitialized mutex attributes object are
undefined.

RETURN VALUE
============

On success, these functions return 0. On error, they return a positive
error number.

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008.

NOTES
=====

Subsequent changes to a mutex attributes object do not affect mutex that
have already been initialized using that object.

SEE ALSO
========

**pthread_mutex_init**\ (3), **pthread_mutexattr_getpshared**\ (3),
**pthread_mutexattr_getrobust**\ (3), **pthreads**\ (7)
