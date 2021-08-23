
<!-- ======================================================================= -->
# the reasoning behind the definition of "presequent"

In regards to (ordered) sequences we can state that:

* The last element of a sequence is subsequent to every other element.

Without the definition of "pre-sequent" we can only state that ..

* The elements of a sequence are subsequent to the first element.

That is, we are forced to flip the order of arguments in that statement. The
issue here is however that the focus of that statement (i.e. the first element)
appears last. Because of that, we have to spend more thought on the second
statement, which is why it can not be understood as easily.

In addition to that, the beginning of that statement (i.e. "the elements of
a sequence") is to some extent inaccurate since at first one lacks the bit of
information that one of these elements (i.e. the first element) can not be
included in that set of elements.

However, with the definition of "pre-sequent" we can state that ..

* (3) The first element of a sequence is presequent to every other element.

And since the order of arguments is maintained, the statement can be understood
more easily. Put differently, the definition of "presequent" allows to make
statements that naturally reflect the corresponding element order (i.e. oriented
from first to last), whereas "subsequent" forces an orientation against that
natural order.

<!-- ======================================================================= -->
## in regards to - node trees

In the context of a node tree we can state that ..

* A leaf is subsequent to its ancestors.
* The root of a tree is presequent to its descendants.

As before, "presequent" reflects the node order of a tree more naturally since
its edges are downwards oriented (i.e. from a root towards its descendants).

Note the difference in the amount of secondary nodes (i.e. those referred to
by the second arguments): A node has a limited amount of ancestors, but may
have any number of descendants.

<!-- ======================================================================= -->
## in regards to - past, present, future

( Imagine a client that receives instructions from a server, one command at
a time. A more general perspective would be that of "a stream of things". )

The following seemingly subtle difference is even more important when we talk
about a linear processes. In this context a process needs to be understood as
a series of operations (or actions) such that "operation A" is required by
"operation B".

That is, if "B" is understood as the next/current/present operation, while
assuming that "B must be subsequent to A" must be satisfied, then a design
must ensure that "A" was already executed. This can be referred to as a
verification step which checks that "A" is an element of the past (i.e.
look back), which, given the required resources, can be detected with ease.

In contrary to that, the statement "A is presequent to B" can be said to imply
that "A" allows to execute "B". However, and since "B" can now be understood
as a possible future event, a process that is currently executing "A" can not
know if, at some later point in time, it will also have to execute "B".

Even though a process may have information that allows to make assumptions
(e.g. based on definitions, or based on heuristics), every action that is
subsequent to "A" remains in general uncertain in regards to "A". And because
one has no guarantee about what will happen in the future (i.e. look ahead),
one can in general not execute any action based on events that may or may happen.

<!-- ======================================================================= -->
## in regards to - forwards/backwards oriented

Given a certain point in time (i.e. some current context), we also use the
word "subsequent" to refer to a group of events that may or may not happen
in the future. That is, based on a given context, one can make a statement
in regards to "subsequent elements".

These one-argument references are as such forward oriented. However, and as
before, the issue with these kind of statements is that future events are
inherently uncertain and can not be relied upon.

In contrary to that, the definition of "presequent" allows to make a statement
in regards to "presequent elements" and is as such backwards oriented. That
is, the term "presequent" also allows to refer to what is in the past and
because of that to what can be relied upon. Put differently, a reference to
to what is guaranteed to exist, or to what can be verified since the events
did already happen.

The term "presequent" therefore allows to shift ones focus from what might
or might not happen, towards what can be guaranteed and verified.
