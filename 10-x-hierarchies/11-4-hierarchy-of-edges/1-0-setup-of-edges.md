
<!-- ======================================================================= -->
# setups of edges

Recall that each edge in a tree is an ordered sequence of nodes. After all,
a tree is such that both of its endpoints must be distinct (i.e. no loops).

<!-- ======================================================================= -->
## a (simple) setup of edges

A set of strings will be referred to as **a (simple) setup** `E`,
if the following requirements are met.

* (R0) `E` is a set/family of strings.
* (R1) `E` is expected to be non-empty.
* (R2) Each edge `(e in E)` must be an ordered sequence.
* (R3) Each edge `(e in E)` must consist of two nodes.
* (R4) `E` must be **a-symmetric**.

Note that each edge `(e in E)` is expected to be an ordered sequence of two
distinct odes. Because of that, edges that have a node as its source and also
as its sink are not allowed (i.e. **no loops**).

* `(a != b)` must be true for any edge `((a,b) in E)`

Note that there must be no edge such that it is reversed to another edge.
Because of that, any simple setup corresponds with a strict partial order,
each of which is transitive and **a-symmetric**. That is, the transitive
closure of a simple setup satisfies the requirements of a strict partial
order relation.

* a-symmetric := if `aEb`, then `!bEa`
* a-symmetric := if `((a,b) in E)`, then `((b,a) not-in E)`

Recall that even the a-symmetric characteristic prevents a set of edges from
having reflexive edges (i.e. loops). That is because a loop is in conflict
with the a-symmetric requirement since both endpoints of such an edge are
then equal.

<!-- ======================================================================= -->
## forming paths over the edges

Since each edge in a setup of edges is an ordered sequence of two endpoints,
and since each such setup is required to be a-symmetric, directed paths over
the edges can be formed as described in the chapters about graphs and trees.
That is, a path over the edges in a setup is a sequence of nodes such that
there is an edge for any pair of consecutive nodes in it.

That is, `p(a,b) := (a,..,b)` is a valid path,
if `( p[i], p[i+1] )` is an edge in `E`
for any index `(i in [1,#p-1])`.

Note that, in addition to a universal set of nodes `U` and a universal graph
`G`, a setup can be understood to be accompanied by **a set of all those paths**
`P` that can be formed over its edges.

* `P` is the set of all valid paths over `E`

Note that `aPb` and `((a,b) in P)` are both true, if there is at least one
path in `P` that begins in `a` and ends in `b`.

* `p(a,b) := { (p := (a,..,b)) | (p in P) }`
* `aPb := (#p(a,b) > 0)`

Note that `p(a,b)` can be used to refer to the path that connects both of its
endpoints, if only one such path can be formed - i.e. if `(#p(a,b) == 1)`.

<!-- ======================================================================= -->
## definition of hierarchy-based terms

Recall that some hierarchy-based terms are defined using edges.

* `(p parent-of c), (c child-of p) := pEc`
* `p(n) := { p | pEn }` and `c(p) := { c | pEc }`
* `(a sibling-of b) := pEa and pEb`

Recall that **a root node** is such that it is a source to an edge,
but no sink to another edge.

* `RN := { r | rEa for some (a in U), but not bEr for any (b in U) }`
* `RN(n) := { r | rPn for some (r in RN) }`
* `(r root-of n) := (r in RN(n))`

Likewise, **a leaf node** is such that it is a sink to an edge,
but no source to another edge.

* `LN := { l | aEl for some (a in U), but not lEb for any (b in U) }`
* `LN(n) := { l | nPl for some (l in LN) }`
* `(l leaf-of n) := (l in LN(n))`

The definition of paths allows to generalize certain aspects.

* `(a presequent-to d), (d subsequent-to a) := aPd`
* `(a ancestor-of d), (d descendant-of a) := aPd`

Based on that, the set of all ancestors `A(n)` and the set of all
descendants `D(n)` of a node `(n in U(E))` can be defined.

* `A(n) := { a | (a ancestor-of n) }`
* `D(n) := { d | (d descendant-of n) }`

<!-- ======================================================================= -->
## characteristics of simple setups

Note that, since a simple setup is not required to be transitive, and even
though loops are not allowed, any simple setup **may still be cyclic**.
That is because, paths over the edges of a setup are not (yet) required to
be ordered sequences of nodes.

Note that a simple setup may contain more than one node that is a source to
an edge, but no sink to another edge (i.e. **any number of root nodes**).
Conversely, more than one node may exist that is a sink to an edge, but no
source to another edge (i.e. **any number of leaf nodes**).

Note that a simple setup may contain nodes that are source nodes to any number
of edges (i.e. "a parent may have **more than one child**"). Likewise, nodes
may exist that are sink nodes to any number of edges (i.e. "a child may have
**more than one parent**").

Note that there are **no disconnected nodes** in a simple setup of edges. That
is because such a setup can only contain a node, if it is an endpoint to one
or more edges.

Note that, since a simple setup does not support disconnected nodes, and since
it also does not support any loops, not every partial order can be expressed
as a simple setup of edges. That is, simple setups only cover a proper subclass
of partial orders to the class of all possible partial orders.

<!-- ======================================================================= -->
## a partial setup of edges

A set of strings will be referred to as **a partial setup** `E`,
if the following requirements are met.

* (R0) `E` is a simple setup of edges.
* (R1) Each path `(p in P)` must be an ordered sequence.
* (R2) `E` must be **downward-total**.

Note that two nodes are said to be **related** with each other, if a path
can be formed that has both nodes as its endpoints. That is, one node must
be an ancestor of the other.

* `(a related-to b) := aPb or bPa` for `(a,b in U(E))` and `(a != b)`

Note that a partial setup is **not required to be transitive**. Because of
that, path-based definitions must be used in order to require characteristics
that are analogous to the order-based definitions of "downward total" and
"overall total".

Note that, since requirement R1 disallows paths that contain repeating nodes,
a partial setup can neither have loops nor cycles. That is, a partial setup
must be **acyclic**, which is why no node is subsequent and also presequent
to another node, including itself.

* if `(aPb or bPa)`, then `(aPb ex-or bPa)` for any pair of nodes

Note that requirement R2 (i.e. must be **downward-total**) requires that all
the nodes, which are presequent to a node, must be related with each other.
That is, any such node must be an ancestor or a descendant to another node in
that subset. Because of that, a partial setup of sets can not have multiple
rooted paths per node and no parallel subcomponents.

* downward-total := `(aPb or bPa)` must be true ..
* for all `(a,b in A(n))` and all `(n in U(E))`

Note that, despite requirement R2, a partial setup of edges may still have
overall more than one root, but must have one and only one root per component.

<!-- ======================================================================= -->
## a total setup of edges

A set of strings will be referred to as **a total setup** `E`,
if the following requirements are met.

* (R0) `E` is a partial setup of edges.
* (R1) `E` must be **upward-total**.

Note that, since a total setup is required to be **downward- and upward-total**,
each parent in a setup must have **one and only one child**. Any non-empty total
setup must therefore have **one root and one leaf only**.
