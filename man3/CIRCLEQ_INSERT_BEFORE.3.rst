lists and tail queues

These macros define and operate on four types of data structures:
singly-linked lists, singly-linked tail queues, lists, and tail queues.
All four structures support the following functionality:

Insertion of a new entry at the head of the list.

Insertion of a new entry after any element in the list.

O(1) removal of an entry from the head of the list.

Forward traversal through the list.

Swapping the contents of two lists.

Singly-linked lists are the simplest of the four data structures and
support only the above functionality. Singly-linked lists are ideal for
applications with large datasets and few or no removals, or for
implementing a LIFO queue. Singly-linked lists add the following
functionality:

O(n) removal of any entry in the list.

Singly-linked tail queues add the following functionality:

Entries can be added at the end of a list.

O(n) removal of any entry in the list.

They may be concatenated.

However:

All list insertions must specify the head of the list.

Each head entry requires two pointers rather than one.

Code size is about 15% greater and operations run about 20% slower than
singly-linked lists.

Singly-linked tail queues are ideal for applications with large datasets
and few or no removals, or for implementing a FIFO queue.

All doubly linked types of data structures (lists and tail queues)
additionally allow:

Insertion of a new entry before any element in the list.

O(1) removal of any entry in the list.

However:

Each element requires two pointers rather than one.

Code size and execution time of operations (except for removal) is about
twice that of the singly-linked data-structures.

Linked lists are the simplest of the doubly linked data structures. They
add the following functionality over the above:

They may be traversed backwards.

However:

To traverse backwards, an entry to begin the traversal and the list in
which it is contained must be specified.

Tail queues add the following functionality:

Entries can be added at the end of a list.

They may be traversed backwards, from tail to head.

They may be concatenated.

However:

All list insertions and removals must specify the head of the list.

Each head entry requires two pointers rather than one.

Code size is about 15% greater and operations run about 20% slower than
singly-linked lists.

In the macro definitions,

is the name of a user defined structure, that must contain a field of
type

or

named

The argument

is the name of a user defined structure that must be declared using the
macros

or

See the examples below for further explanation of how these macros are
used.

A singly-linked list is headed by a structure defined by the

macro. This structure contains a single pointer to the first element on
the list. The elements are singly linked for minimum space and pointer
manipulation overhead at the expense of O(n) removal for arbitrary
elements. New elements can be added to the list after an existing
element or at the head of the list. An

structure is declared as follows:

SLIST_HEAD(HEADNAME, TYPE) head;

where

is the name of the structure to be defined, and

is the type of the elements to be linked into the list. A pointer to the
head of the list can later be declared as:

struct HEADNAME \*headp;

(The names

and

are user selectable.)

The macro

evaluates to an initializer for the list

The macro

evaluates to true if there are no elements in the list.

The macro

declares a structure that connects the elements in the list.

The macro

returns the first element in the list or NULL if the list is empty.

The macro

traverses the list referenced by

in the forward direction, assigning each element in turn to

The macro

initializes the list referenced by

The macro

inserts the new element

at the head of the list.

The macro

inserts the new element

after the element

The macro

returns the next element in the list.

The macro

removes the element

from the head of the list. For optimum efficiency, elements being
removed from the head of the list should explicitly use this macro
instead of the generic

macro.

The macro

removes the element

from the list.

SLIST_HEAD(slisthead, entry) head = SLIST_HEAD_INITIALIZER(head); struct
slisthead \*headp; /\* Singly-linked List head. \*/ struct entry { ...
SLIST_ENTRY(entry) entries; /\* Singly-linked List. \*/ ... } \*n1,
\*n2, \*n3, \*np;

SLIST_INIT(&head); /\* Initialize the list. \*/

n1 = malloc(sizeof(struct entry)); /\* Insert at the head. \*/
SLIST_INSERT_HEAD(&head, n1, entries);

n2 = malloc(sizeof(struct entry)); /\* Insert after. \*/
SLIST_INSERT_AFTER(n1, n2, entries);

SLIST_REMOVE(&head, n2, entry, entries);/\* Deletion. \*/ free(n2);

n3 = SLIST_FIRST(&head); SLIST_REMOVE_HEAD(&head, entries); /\* Deletion
from the head. \*/ free(n3); /\* Forward traversal. \*/
SLIST_FOREACH(np, &head, entries) np-> ...

while (!SLIST_EMPTY(&head)) { /\* List Deletion. \*/ n1 =
SLIST_FIRST(&head); SLIST_REMOVE_HEAD(&head, entries); free(n1); }

A singly-linked tail queue is headed by a structure defined by the

macro. This structure contains a pair of pointers, one to the first
element in the tail queue and the other to the last element in the tail
queue. The elements are singly linked for minimum space and pointer
manipulation overhead at the expense of O(n) removal for arbitrary
elements. New elements can be added to the tail queue after an existing
element, at the head of the tail queue, or at the end of the tail queue.
A

structure is declared as follows:

STAILQ_HEAD(HEADNAME, TYPE) head;

where

is the name of the structure to be defined, and

is the type of the elements to be linked into the tail queue. A pointer
to the head of the tail queue can later be declared as:

struct HEADNAME \*headp;

(The names

and

are user selectable.)

The macro

evaluates to an initializer for the tail queue

The macro

concatenates the tail queue headed by

onto the end of the one headed by

removing all entries from the former.

The macro

evaluates to true if there are no items on the tail queue.

The macro

declares a structure that connects the elements in the tail queue.

The macro

returns the first item on the tail queue or NULL if the tail queue is
empty.

The macro

traverses the tail queue referenced by

in the forward direction, assigning each element in turn to

The macro

initializes the tail queue referenced by

The macro

inserts the new element

at the head of the tail queue.

The macro

inserts the new element

at the end of the tail queue.

The macro

inserts the new element

after the element

The macro

returns the next item on the tail queue, or NULL this item is the last.

The macro

removes the element at the head of the tail queue. For optimum
efficiency, elements being removed from the head of the tail queue
should use this macro explicitly rather than the generic

macro.

The macro

removes the element

from the tail queue.

STAILQ_HEAD(stailhead, entry) head = STAILQ_HEAD_INITIALIZER(head);
struct stailhead \*headp; /\* Singly-linked tail queue head. \*/ struct
entry { ... STAILQ_ENTRY(entry) entries; /\* Tail queue. \*/ ... } \*n1,
\*n2, \*n3, \*np;

STAILQ_INIT(&head); /\* Initialize the queue. \*/

n1 = malloc(sizeof(struct entry)); /\* Insert at the head. \*/
STAILQ_INSERT_HEAD(&head, n1, entries);

n1 = malloc(sizeof(struct entry)); /\* Insert at the tail. \*/
STAILQ_INSERT_TAIL(&head, n1, entries);

n2 = malloc(sizeof(struct entry)); /\* Insert after. \*/
STAILQ_INSERT_AFTER(&head, n1, n2, entries); /\* Deletion. \*/
STAILQ_REMOVE(&head, n2, entry, entries); free(n2); /\* Deletion from
the head. \*/ n3 = STAILQ_FIRST(&head); STAILQ_REMOVE_HEAD(&head,
entries); free(n3); /\* Forward traversal. \*/ STAILQ_FOREACH(np, &head,
entries) np-> ... /\* TailQ Deletion. \*/ while (!STAILQ_EMPTY(&head)) {
n1 = STAILQ_FIRST(&head); STAILQ_REMOVE_HEAD(&head, entries); free(n1);
} /\* Faster TailQ Deletion. \*/ n1 = STAILQ_FIRST(&head); while (n1 !=
NULL) { n2 = STAILQ_NEXT(n1, entries); free(n1); n1 = n2; }
STAILQ_INIT(&head);

A list is headed by a structure defined by the

macro. This structure contains a single pointer to the first element on
the list. The elements are doubly linked so that an arbitrary element
can be removed without traversing the list. New elements can be added to
the list after an existing element, before an existing element, or at
the head of the list. A

structure is declared as follows:

LIST_HEAD(HEADNAME, TYPE) head;

where

is the name of the structure to be defined, and

is the type of the elements to be linked into the list. A pointer to the
head of the list can later be declared as:

struct HEADNAME \*headp;

(The names

and

are user selectable.)

The macro

evaluates to an initializer for the list

The macro

evaluates to true if there are no elements in the list.

The macro

declares a structure that connects the elements in the list.

The macro

returns the first element in the list or NULL if the list is empty.

The macro

traverses the list referenced by

in the forward direction, assigning each element in turn to

The macro

initializes the list referenced by

The macro

inserts the new element

at the head of the list.

The macro

inserts the new element

after the element

The macro

inserts the new element

before the element

The macro

returns the next element in the list, or NULL if this is the last.

The macro

removes the element

from the list.

LIST_HEAD(listhead, entry) head = LIST_HEAD_INITIALIZER(head); struct
listhead \*headp; /\* List head. \*/ struct entry { ...
LIST_ENTRY(entry) entries; /\* List. \*/ ... } \*n1, \*n2, \*n3, \*np,
\*np_temp;

LIST_INIT(&head); /\* Initialize the list. \*/

n1 = malloc(sizeof(struct entry)); /\* Insert at the head. \*/
LIST_INSERT_HEAD(&head, n1, entries);

n2 = malloc(sizeof(struct entry)); /\* Insert after. \*/
LIST_INSERT_AFTER(n1, n2, entries);

n3 = malloc(sizeof(struct entry)); /\* Insert before. \*/
LIST_INSERT_BEFORE(n2, n3, entries);

LIST_REMOVE(n2, entries); /\* Deletion. \*/ free(n2); /\* Forward
traversal. \*/ LIST_FOREACH(np, &head, entries) np-> ...

while (!LIST_EMPTY(&head)) { /\* List Deletion. \*/ n1 =
LIST_FIRST(&head); LIST_REMOVE(n1, entries); free(n1); }

n1 = LIST_FIRST(&head); /\* Faster List Deletion. \*/ while (n1 != NULL)
{ n2 = LIST_NEXT(n1, entries); free(n1); n1 = n2; } LIST_INIT(&head);

A tail queue is headed by a structure defined by the

macro. This structure contains a pair of pointers, one to the first
element in the tail queue and the other to the last element in the tail
queue. The elements are doubly linked so that an arbitrary element can
be removed without traversing the tail queue. New elements can be added
to the tail queue after an existing element, before an existing element,
at the head of the tail queue, or at the end of the tail queue. A

structure is declared as follows:

TAILQ_HEAD(HEADNAME, TYPE) head;

where

is the name of the structure to be defined, and

is the type of the elements to be linked into the tail queue. A pointer
to the head of the tail queue can later be declared as:

struct HEADNAME \*headp;

(The names

and

are user selectable.)

The macro

evaluates to an initializer for the tail queue

The macro

concatenates the tail queue headed by

onto the end of the one headed by

removing all entries from the former.

The macro

evaluates to true if there are no items on the tail queue.

The macro

declares a structure that connects the elements in the tail queue.

The macro

returns the first item on the tail queue or NULL if the tail queue is
empty.

The macro

traverses the tail queue referenced by

in the forward direction, assigning each element in turn to

is set to

if the loop completes normally, or if there were no elements.

The macro

traverses the tail queue referenced by

in the reverse direction, assigning each element in turn to

The macro

initializes the tail queue referenced by

The macro

inserts the new element

at the head of the tail queue.

The macro

inserts the new element

at the end of the tail queue.

The macro

inserts the new element

after the element

The macro

inserts the new element

before the element

The macro

returns the last item on the tail queue. If the tail queue is empty the
return value is

The macro

returns the next item on the tail queue, or NULL if this item is the
last.

The macro

returns the previous item on the tail queue, or NULL if this item is the
first.

The macro

removes the element

from the tail queue.

The macro

swaps the contents of

and

TAILQ_HEAD(tailhead, entry) head = TAILQ_HEAD_INITIALIZER(head); struct
tailhead \*headp; /\* Tail queue head. \*/ struct entry { ...
TAILQ_ENTRY(entry) entries; /\* Tail queue. \*/ ... } \*n1, \*n2, \*n3,
\*np;

TAILQ_INIT(&head); /\* Initialize the queue. \*/

n1 = malloc(sizeof(struct entry)); /\* Insert at the head. \*/
TAILQ_INSERT_HEAD(&head, n1, entries);

n1 = malloc(sizeof(struct entry)); /\* Insert at the tail. \*/
TAILQ_INSERT_TAIL(&head, n1, entries);

n2 = malloc(sizeof(struct entry)); /\* Insert after. \*/
TAILQ_INSERT_AFTER(&head, n1, n2, entries);

n3 = malloc(sizeof(struct entry)); /\* Insert before. \*/
TAILQ_INSERT_BEFORE(n2, n3, entries);

TAILQ_REMOVE(&head, n2, entries); /\* Deletion. \*/ free(n2); /\*
Forward traversal. \*/ TAILQ_FOREACH(np, &head, entries) np-> ... /\*
Reverse traversal. \*/ TAILQ_FOREACH_REVERSE(np, &head, tailhead,
entries) np-> ... /\* TailQ Deletion. \*/ while (!TAILQ_EMPTY(&head)) {
n1 = TAILQ_FIRST(&head); TAILQ_REMOVE(&head, n1, entries); free(n1); }
/\* Faster TailQ Deletion. \*/ n1 = TAILQ_FIRST(&head); while (n1 !=
NULL) { n2 = TAILQ_NEXT(n1, entries); free(n1); n1 = n2; }

TAILQ_INIT(&head); n2 = malloc(sizeof(struct entry)); /\* Insert before.
\*/ CIRCLEQ_INSERT_BEFORE(&head, n1, n2, entries); /\* Forward
traversal. \*/ for (np = head.cqh_first; np != (void \*)&head; np =
np->entries.cqe_next) np-> ... /\* Reverse traversal. \*/ for (np =
head.cqh_last; np != (void \*)&head; np = np->entries.cqe_prev) np-> ...
/\* Delete. \*/ while (head.cqh_first != (void \*)&head)
CIRCLEQ_REMOVE(&head, head.cqh_first, entries);

Not in POSIX.1, POSIX.1-2001 or POSIX.1-2008. Present on the BSDs.

functions first appeared in
