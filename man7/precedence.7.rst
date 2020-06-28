NAME
====

operator - C operator precedence and order of evaluation

DESCRIPTION
===========

This manual page lists C operators and their precedence in evaluation.

=================================== ============= =====
Operator                            Associativity Notes
() [] -> . ++ --                    left to right [1]
! ~ ++ -- + - (type) \* & sizeof    right to left [2]
\* / %                              left to right 
+ -                                 left to right 
<< >>                               left to right 
< <= > >=                           left to right 
== !=                               left to right 
&                                   left to right 
^                                   left to right 
\|                                  left to right 
&&                                  left to right 
\|\|                                left to right 
?:                                  right to left 
= += -= \*= /= %= <<= >>= &= ^= \|= right to left 
,                                   left to right 
=================================== ============= =====

The following notes provide further information to the above table:

-  The ++ and -- operators at this precedence level are the postfix
   flavors of the operators.

-  The ++ and -- operators at this precedence level are the prefix
   flavors of the operators.
