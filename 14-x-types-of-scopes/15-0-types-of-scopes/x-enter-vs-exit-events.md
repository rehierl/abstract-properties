
<!-- ======================================================================= -->
## the exit-events of nodes and scopes

Even though an implementation can be expected to detect a defining node and its
associated scope with ease (e.g. a specific attribute set on a start-tag), there
is still the issue of having to detect the end of a scope. It is however not
possible to define the end of a scope in terms of a specific last node. That is
because each node may in general have any number of descendants. In addition to
that, and due to possible input errors, such last nodes can not be guaranteed
to even exist.

However, since the above types of scopes are defined based upon sub-orders that
are embedded into the trace of a tree, and as such consistently oriented (i.e.
the edges are oriented the same way), **the last node of a scope is the last
node of a sub-order** (i.e. the last leaf of an induced suffix) in the trace of
a tree. Implementations must therefore have the means to detect such last nodes.

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-| type-0                                    t0[n]
t1-scope(n)            |-type-1--------|                             t1/U[n]
t2-scope(n)            |-type-2-------------------------|            t2/O[n]
t3-scope(n)            |-type-3--------------------------- ... -|    t3[n]
```

Recall that a start-tag corresponds with its defining node. In contrary to that,
an **end-tag** does not correspond with any node in particular. In other words,
and since an end-tag appears to be located in between two nodes, they only mark
the end of well-defined groups of nodes. Furthermore, the end-tag of a parent
marks the end of one or more such groups. After all, the end-tag of a tree's
root marks the end of the root's type-1 scope, the end of all type-2 scopes of
its child nodes, and the end of all type-3 scopes of all the other nodes.

Note that, from a strict point of view, each node is **entered**, **visited**
and **exited** while no other node is still in the process of being visited.
To be more accurate, the visit of a node must be understood as **an indivisible
atomic operation**. Also, the visit of a node is said to trigger the enter-
and the exit-event of a node.

Since the exit event of a node corresponds with the exit event of the node's
type-0 scope, and an end-tag of a node with the exit-event of its type-1 scope,
implementations must map the abstract exit events of non-null scopes onto the
exit events of type-1 scopes. That is because the tag-based syntax does not
include tags that are dedicated to the ends of type-2 and type-3 scopes.

* node-exit <=> type-0 scope-exit
* end-tag <=> type-1/2/3 scope-exit

Note that the node whose type-1 exit event will be used to close a particular
(default) scope, will be referred to as the scope's **parent container**.

```
    |<- enter node n, determine the scope's type ->|
.. <n> .......................................... </x> ..
    |-> and associate it with end-tag '</x>'       | onVisit(n)
    |                            close the scope <-| onExitT1(x)
```

Since each scope begins with the start-tag of its defining node and may end
with the end-tag of another node (i.e. not necessarily tags of the same node),
an implementation must maintain a memory of those events it encountered in the
past in order to determine which of the remaining open scopes to close when a
particular end-tag is reached. Based on that, end-tags can be said to be
**backwards oriented** (i.e. against the edges, i.e. towards past events).

Note that the following pseudo-code example is in regards to regular properties,
each of which is associated with one of the previously defined types of scopes.
