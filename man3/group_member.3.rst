NAME
====

group_member - test whether a process is in a group

SYNOPSIS
========

**#include <unistd.h>**

**int group_member(gid_t**\ *gid*\ **);**

Feature Test Macro Requirements for glibc (see
**feature_test_macros**\ (7)):

**group_member**\ (): \_GNU_SOURCE

DESCRIPTION
===========

The **group_member**\ () function tests whether any of the caller's
supplementary group IDs (as returned by **getgroups**\ (2)) matches
*gid*.

RETURN VALUE
============

The **group_member**\ () function returns nonzero if any of the caller's
supplementary group IDs matches *gid*, and zero otherwise.

CONFORMING TO
=============

This function is a nonstandard GNU extension.

SEE ALSO
========

**getgid**\ (2), **getgroups**\ (2), **getgrouplist**\ (3),
**group**\ (5)
