
<!-- ======================================================================= -->
# The scope of a node

The following defines the scope of a node in regards to specific node orders.
Because of that, and depending on a given context (i.e. a given node order),
each node can be understood to be associated with several distinct scopes.

Note that the scope of a node can be understood as a general area-of-effect
(AOE). Also, subsequent discussions will build upon these scopes to define
the scopes of operations and properties.

<!-- ======================================================================= -->
## a suffix-based perspective on induced subtrees

```
N(T)  := { .., p, fs, .., ps, n, fc, .., lc, ns, .., ls, .. }
```

Given a general graph `t0` that has no edges, then no descendants can be
reached from any given vertex. Because of that, the induced subgraph of
a vertex (i.e. `t0[v]`) in such a context consists of a single vertex.

Put differently, `t0[n]` is an induced subtree if none of the descendants
of the specified node is to be included. As such, these reference could be
referred to as 1-node induced subtrees.

```
|-t0[n]-|
|   n   |
|-------|
```

Note that digit `0` in reference `t0[n]` can be understood to state that
no set of edges is included. Based on that, digit `1` can be said to refer
to an un-ordered tree. That is, after the addition of all the edges in the
initial un-ordered tree (i.e. the 1st set of edges).

```
|-t1[n]-----|
|    |=> fc |
| n =|=> .. |
|    |=> lc |
|-----------|
```

After that, one can assume that the set of edges `E1` of an un-ordered tree
are to be included. That is, a node can in general be said to be connected to
all the nodes that can be reached over a path of nodes over the edges in the
un-ordered tree that begins in the corresponding node. Because of that, the
induced subtree of a node (i.e. `t1[n]`) has in general more than one node.

Recall that a leaf has no descendants. Because of that, the induced subtree
of a leaf in the ordered tree remains unchanged (i.e. `(t1[n] == t0[n])`).

```
|-t2[n]-----------|
| n =|=> fc .. lc |
|    |=> ns .. ls |
|-----------------|
```

One can then assume that a child order is added to the un-ordered tree as a
2nd set of edges `E2` (hence: `t2[n]`). Based on that, a node can in general
be said to gain additional descendants.

Note that `t1[n]` is embedded into `t2[n]` as a partial sub-order, not as an
actual sub-tree. Also, `t2[n]` includes the former subsequent siblings of a
node and all of their descendants.

Note that a `tN[n]` reference needs to be understood in regards to the node
tree that results from forming the transitive reduction of the union of all
the sets of edges involved (i.e. from the 1st set `E1` to the N-th set `EN`).

```
        |-t3[n]-------------------------------------|
r => .. | n => (fc .. lc ..) => (ns .. ls ..) => .. |
        |-------------------------------------------|
```

Recall that the statement of an additional edge must not be in conflict with
the statements of already existing edges. That is, the addition of further
edges to an existing set of edges must not form loops or cycles. Because of
that, no more edge can be added, if the existing edges combined can be said
to form a total order (i.e. a trace of nodes).

Since more and more edges can be added until the node order of an un-ordered
tree is transformed into a total order, the number of descendants that can be
reached from a given node keeps growing until all the nodes that are subsequent
to the starting node in the resulting total order are included. The induced
subtree of a node in the resulting total order is therefore a suffix to that
node order.

With that in mind, an induced subtree can be said to include a node and all
the nodes that are subsequent to it in the corresponding node order. In regards
to a given order, an induced subtree can therefore be seen as a suffix to that
node order. Based on that, this generic point of view will be referred to as
**an iterative**, or as **a suffix-based perspective** on induced subtrees.
Also, an induced subtree (i.e. a graph-based perspective) may in general be
referred to as **an induced suffix** (i.e. an order-based perspective).

Recall that the pre-order trace of a tree is formed by prefixing the sequence
of former subsequent siblings of a node by its sequence of former child nodes.
This is achieved by adding a new edge in between the last child of a node and
the node's next subsequent sibling. All of these additional edges can be said
to form the third set of edges `E3`, which represents the application of the
pre-order rule to all the nodes in the ordered tree. As stated before, all the
edges in `E3` transform the ordered tree into the pre-order trace (i.e. a total
order). Because of that, the induced subtree of a node `t3[n]` is a suffix to
the tree's pre-order trace (i.e. an induced suffix).

<!-- ======================================================================= -->
## the scopes of a node

Recall that **the scope of a tag** is understood to include the defining node
of a tag (e.g. node `n`) and all of its descendants. The term "scope of a tag"
can therefore be understood to refer to the corresponding set of nodes.

* for `<n> fc .. lc .. </n>`

As such, the scope of a tag can be defined as the set of nodes in the pre-order
trace of the tag's defining node. The scope of a tag therefore corresponds with
the set of nodes of the induced subtree of the tag's defining node in the
un-ordered tree.

* `scope(<n>) := E(traceU(n)) := N(t1[n])`

Similar to that, **the scope of a node** can in general be understood as
a well-defined general area-of-effect (in short **AOE**). The following
types of scopes can be distinguished.

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-|
t1-scope(n)            |-type-1--------|
t2-scope(n)            |-type-2-------------------------|
t3-scope(n)            |-type-3--------------------------- ... -|
```

**t0, type-0:** The scope is restricted to the defining node.
As such, it contains none of the node's descendants (hence "type-0").

**t1, type-1:** The scope extends the type-0 scope by the node's descendants
in the un-ordered tree. That is, the type-1 scope of node `n` is the set of
nodes in the induced subtree `t1[n]` (i.e. `N(t1[n])`).

**t2, type-2:** The scope extends the node's type-1 scope by the additional
descendants in the ordered tree. That is, the type-2 scope of node `n` is
the set of nodes in the induced subtree `t2[n]` (i.e. `N(t2[n])`).

**t3, type-3:** The scope extends the node's type-2 scope by the additional
descendants in the tree's pre-order trace. That is, the type-3 scope of node
`n` is the set of nodes in the induced suffix `t3[n]` (i.e. `N(t3[n])`).

* `t0-scope(n) := N(t0[n]) := {n}`
* `t1-scope(n) := N(t1[n]) := E(traceU(n))`
* `t2-scope(n) := N(t2[n]) := E(traceO(n))`
* `t3-scope(n) := N(t3[n])`
* `scope(<n>) := t1-scope(n)`

<!-- ======================================================================= -->
## remarks

Note that the types of scopes introduced above are such that the next type is
defined by including some of the nodes the previous type did not cover. That
is, these types build upon each other since they are defined based upon the
iterative addition of more and more non-conflicting edges.

* `(t0-scope(n) subset-of t1-scope(n))`
* `(t1-scope(n) subset-of t2-scope(n))`
* `(t2-scope(n) subset-of t3-scope(n))`

Note that each scope can be understood to define a substring in the pre-order
trace of a tree. Based on that, the `t0` scope of a node can be understood as
a prefix to the node's `t1` scope.

* `(t0-scope(n) prefix-of t1-scope(n))`
* `(t1-scope(n) prefix-of t2-scope(n))`
* `(t2-scope(n) prefix-of t3-scope(n))`

Note that, in the pre-order trace of a tree, a type-0 scope begins and ends
with the start-tag of the defining node. In contrary to that, a type-1 scope
**ends with the end-tag** of the defining node (i.e. `</n>`), a type-2 scope
with the end-tag of the corresponding parent node (i.e. `</p>`), and type-3
scope with the end-tag of the tree's root (i.e. `</r>`).

Note that the scope of a node can not exist without its defining node.
The scope of a node is therefore **always non-empty**.

Note that one or more of these types of scopes may refer to the same set of
nodes. For example, all three scopes are the same if the defining node is
a node in the un-ordered tree that has no child nodes (i.e. a leaf) and no
subsequent sibling (i.e. a last child, i.e. a leaf in the ordered tree).
