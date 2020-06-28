NAME
====

group - user group file

DESCRIPTION
===========

The */etc/group* file is a text file that defines the groups on the
system. There is one entry per line, with the following format:

::

   group_name:password:GID:user_list

The fields are as follows:

*group_name*
   the name of the group.

*password*
   the (encrypted) group password. If this field is empty, no password
   is needed.

*GID*
   the numeric group ID.

*user_list*
   a list of the usernames that are members of this group, separated by
   commas.

FILES
=====

*/etc/group*

BUGS
====

As the 4.2BSD **initgroups**\ (3) man page says: no one seems to keep
*/etc/group* up-to-date.

SEE ALSO
========

**chgrp**\ (1), **gpasswd**\ (1), **groups**\ (1), **login**\ (1),
**newgrp**\ (1), **sg**\ (1), **getgrent**\ (3), **getgrnam**\ (3),
**gshadow**\ (5), **passwd**\ (5), **vigr**\ (8)
