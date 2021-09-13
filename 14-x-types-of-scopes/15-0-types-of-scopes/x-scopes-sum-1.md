
Recall that the scope of a tag contains its defining node and its descendants
in the un-ordered tree. Scopes can therefore in general be said to be formed
from node orders (i.e. sets of nodes that are associated with sets of edges
such that the edges define an order operator). Based on that generic point of
view, the description "type-x scope of a node" can be defined.

If one begins with a simple set of nodes (i.e. no edges), one can add the first
set of edges (i.e. those in the un-ordered tree). After that, one can add the
second set of edges (i.e. those in the child orders). Finally, one can add a
third set of edges (i.e. those defined by the pre-order rule). Based on that,
each node can be understood to be associated with multiple distinct of scopes,
each of which builds upon the previous ones.

Note that the iterative addition of more and more edges must not add edges that
are in conflict with existing ones. That is, a node can not be presequent and
subsequent to another node, not even to itself (i.e. no loops and no cycles).

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-| type-0                                    | t0[n]
t1-scope(n)            |-type-1--------|                             | t1/U[n]
t2-scope(n)            |-type-2-------------------------|            | t2/O[n]
t3-scope(n)            |-type-3--------------------------- ... -|    | t3[n]
```

**t0, type-0:** The scope is restricted to the defining node.
As such, it contains none of the node's descendants (hence "type-0").

**t1, type-1:** The scope extends a type-0 scope by the additional descendants
of the node in the un-ordered tree. That is, the type-1 scope of node `n` is
the set of nodes in the **induced subtree** `t1[n]` (i.e. `N(t1[n])`).

**t2, type-2:** The scope extends a type-1 scope by the additional descendants
in the ordered tree. That is, the type-2 scope of node `n` is the set of nodes
in the induced subtree `t2[n]` (i.e. `N(t2[n])`).

**t3, type-3:** The scope extends a type-2 scope by the additional descendants
in the tree's pre-order trace. That is, the type-3 scope of node `n` is the set
of nodes in the **induced suffix** `t3[n]` (i.e. `N(t3[n])`).

Note that, in the pre-order trace of a tree, a type-0 scope begins and ends
with the start-tag of the defining node. In contrary to that, a type-1 scope
**ends with the end-tag** of the defining node (i.e. `</n>`), a type-2 scope
with the end-tag of the corresponding parent node (i.e. `</p>`), and finally
a type-3 scope with the end-tag of the tree's root (i.e. `</r>`).

Note that a type-1 scope may also be referred to as a **null** scope, which
allows to refer to all the other types of scopes as **non-null** scopes.

Based on the iterative formation of these types of scopes, induced subtrees can
be understood from **an order/suffix-based perspective**. That is, an induced
subtree (i.e. a graph-based perspective) may also be referred to as an induced
suffix (i.e. an order-based perspective).

Since each type begins with a defining node and includes all of its descendants
in the corresponding node order, it seems to be more accurate to describe the
scope of a node from an order-based perspective. That is, the scope of a node
**begins with the defining node and contains all the nodes subsequent to it**.

Note that the scope of a node can not exist without its defining node.
That is, the scope of a node is **never empty** (i.e. always **non-empty**).

Note that the scopes of a node represent **well-defined subsets of nodes**,
each of which can be understood as a general **area-of-effect (AOE)**.
