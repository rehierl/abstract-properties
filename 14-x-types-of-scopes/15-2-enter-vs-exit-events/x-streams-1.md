
Based on that, an implementation can be assumed to reach the defining node of
a scope and to have the means to determine the scope's type. From that point
on, an implementation will continue to travel along the edges until the scope's
last node is reached. Hence, a scope has a first node (i.e. its defining node),
a last node, and includes every other node in between. With that in mind,
**scopes are required to be substrings** (i.e. continuous sub-sequences of
nodes) to a pre-order trace.

Note that, as substrings to a pre-order trace, scopes can in general be said to
be closed **intervals** over the pre-order trace of a tree (i.e. `[first,last]`).
And since a pre-order trace is an ordered sequence of nodes, each scope has an
**offset and a length** in regards to such a trace. Based on that, relationships
between scopes can be defined (e.g. a child order).

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 )  | - a pre-order trace
 |-prefix---||-scope--------||-suffix----|   |
 |-unknown--||-open---------||-closed----|   | - a stream-based perspective
             enter       exit                |
                                             |
s(p) := [n4,n7] := ( n4, n5, n6, n7 )        | - visualized definitions
N(p) := E(s(p)) := { n4, n5, n6, n7 }        |
prefix := [n1,n3], suffix := [n8,n10]        |
```

Since scopes are non-empty substrings to a pre-order trace, scopes can be
visualized by **underlining all the nodes in a scope**. (Note that each such
line can be said to represent a unique property/id/reference. Note also that
this visualization suggests a close relationship with **Turing Machines** -
i.e. an input tape and one or more output tapes).

When reaching the defining node of a scope, an implementation can be said to
create a new property it will use to tag/mark the nodes in that scope. From
that point on, the scope counts as being **open (for associations)**. That
is, beginning with a scope's first node (i.e. its defining node), up to and
including a scope's last node, an implementation will set that property as
a property of these nodes. As soon as the scope's last node is reached, the
scope counts as being **closed**. Based on that, an implementation's point
of view on a scope is **a stream-based perspective**, which is why each scope
can be said to be associated with **an open/enter and a close/exit event**.

Note that, due to the stream-based perspective, an implementation can be said
to **propagate a property along the edges** of a pre-order trace. In other
words, each property can in general be said to **emanate** from its defining
node and to be **passed on to** those nodes that are subsequent to it.

If the trace of a tree is processed as described above, then an implementation
can in general determine for each node whether or not that node is within a
given scope. That is because an implementation then only needs to verify if
the corresponding property is set as one of the node's properties.

Note that it is in principle non-relevant in which order the nodes in a scope
are associated. That is because these properties effectively represent simple
truth values (i.e. inside-of/outside-of) that are set on all the nodes within
a scope. Because of that, implementations are not required to store an
order-of-association.
