NAME
====

sched_setparam, sched_getparam - set and get scheduling parameters

SYNOPSIS
========

::

   #include <sched.h>

   int sched_setparam(pid_t pid, const struct sched_param *param);

   int sched_getparam(pid_t pid, struct sched_param *param);

   struct sched_param {
       ...
       int sched_priority;
       ...
   };

DESCRIPTION
===========

**sched_setparam**\ () sets the scheduling parameters associated with
the scheduling policy for the thread whose thread ID is specified in
*pid*\ **.** If *pid*\ **is zero, then** the parameters of the calling
thread are set. The interpretation of the argument *param*\ **depends on
the scheduling** policy of the thread identified by *pid*. See
**sched**\ (7) for a description of the scheduling policies supported
under Linux.

**sched_getparam**\ () retrieves the scheduling parameters for the
thread identified by *pid*\ **.** If *pid*\ **is zero, then the
parameters** of the calling thread are retrieved.

**sched_setparam**\ () checks the validity of *param*\ **for the
scheduling policy of the** thread. The value
*param->sched_priority*\ **must lie within the** range given by
**sched_get_priority_min**\ (2) and **sched_get_priority_max**\ (2).

For a discussion of the privileges and resource limits related to
scheduling priority and policy, see **sched**\ (7).

POSIX systems on which **sched_setparam**\ () and **sched_getparam**\ ()
are available define **\_POSIX_PRIORITY_SCHEDULING** in
*<unistd.h>*\ **.**

RETURN VALUE
============

On success, **sched_setparam**\ () and **sched_getparam**\ () return 0.
On error, -1 is returned, and *errno* is set appropriately.

ERRORS
======

**EINVAL**
   Invalid arguments: *param* is NULL or *pid* is negative

**EINVAL**
   (**sched_setparam**\ ()) The argument *param*\ **does not make sense
   for the current** scheduling policy.

**EPERM**
   (**sched_setparam**\ ()) The caller does not have appropriate
   privileges (Linux: does not have the **CAP_SYS_NICE** capability).

**ESRCH**
   The thread whose ID is *pid*\ **could not be found.**

CONFORMING TO
=============

POSIX.1-2001, POSIX.1-2008.

SEE ALSO
========

**getpriority**\ (2), **gettid**\ (2), **nice**\ (2),
**sched_get_priority_max**\ (2), **sched_get_priority_min**\ (2),
**sched_getaffinity**\ (2), **sched_getscheduler**\ (2),
**sched_setaffinity**\ (2), **sched_setattr**\ (2),
**sched_setscheduler**\ (2), **setpriority**\ (2),
**capabilities**\ (7), **sched**\ (7)
