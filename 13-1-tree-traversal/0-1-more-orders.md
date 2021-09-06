
<!-- ======================================================================= -->
# Embedding more node orders

The embedding of the child order of an unordered doctree into its node order
yields the true node order of the ordered doctree. That node order is such that
it is order preserving in regards to the initial tree order and also in regards
to the doctree's child order. In other words, both node orders are embedded
into the ordered doctree.

In addition to that, an embedding of a doctree's child order has the effect
of reducing the overall amount of incomparable nodes. That is, fewer nodes
remain such that no path can be formed in between two such nodes. Because
of that, the resulting ordered doctree has no more than two child nodes per
parent.

Based on that, one can assume that even more node orders can be embedded until
there are no incomparable nodes left. That is, until the resulting node order
is total and its cover graph therefore a path graph.

<!-- ======================================================================= -->
## topological sorting/ordering

Recall that the process of serializing a DAG such as a tree `T(N,E)` into
**a trace of nodes** `s` can be described as a "topological ordering" if the
relative order of the endpoints of all paths over `T` is preserved in `s`.

* `aPb -> (idx(a) < idx(b))`

Note that more than one such ordering may be possible. One and only one such
ordering is possible, if the node tree is a path graph. In that case, the
ordering is equal to the rooted path of its only leaf.

* `T(N,E)` where `E := {(1,2),(1,3)}`
* `(1,2,3)` and `(1,3,2)` are both valid orderings

<!-- ======================================================================= -->
## partial/linear extension

Recall that a trace of nodes is an ordered sequence of nodes such that it
contains each node of a tree once and once only. Because of that, a trace
of nodes can be understood to define a total order over the tree's set of
nodes.

With that in mind, the embedding of the child order of a doctree (T1) into
its node order can be described as **a partial extension** since the resulting
node tree (T2) will in general not correspond with a total node order (i.e.
no path graph). Despite that, the resulting node tree is order maintaining

* `aPb -> aQb` for `(P over T1)` and `(Q over T2)`

Since the embedding of a child order has the effect of reducing the amount
of incomparable nodes, one can embed even more node orders. Such an embedding
can be described as **a linear extension**, if the resulting node order is
total. Put differently, if the resulting node tree is a path graph.

Note that the difference between "topological ordering" and "linear extension"
is the overall context of both descriptions. That is, "topological ordering"
is in regards to graphs and "linear extension" in regards to partial orders.

<!-- ======================================================================= -->
## requirements

Recall that the underlying strict partial order of a tree is transitive and
a-symmetric. In addition to that, a strict total order is trichotomous.

* transitive := if `aRb` and `bRc`, then also `aRc`
* a-symmetric := if `aRb`, then `!bRa`
* trichotomous := `aRb` exor `bRa` exor `(a == b)` for all `(a,b in R)`

Assuming a cover relation `R(N,E)`, which is intended to be embedded into the
node order of a tree `T(N,E)`, then the following must be taken into account.

(*) `R` may contain an edge `aEb`, even though a path `aPb` can be formed
over `T`. That is because `aEb` is already included in the tree's node order.

(*) If a path `aPb` can be formed over `T`, then `R` must not contain an edge
`bEa`. That is because the edge would otherwise establish a cycle, which is why
the order embedding could then ultimately not result in a total order. After
all, the transitive closure would then produce one or more symmetric edges.

Recall that each tree, and therefore also each path graph, corresponds with
a hierarchy of scopes. Consequently, cycles of any kind can not be supported
since no set can be a superset and also a subset to another set. Based on that,
conflicting statements such as "(a presequent-to b) and (a subsequent-to b)"
can not be allowed.

Due to the above, and for `R` to result in a valid extension, an edge `aEb` can
only be included if neither a path `aPb` nor a path `bPa` can be formed over `T`.
Because of that, the endpoints of an edge in `R` must be disconnected in `T`.
That is, **both endpoints must be incomparable** in `T`.

<!-- ======================================================================= -->
## order maintaining

Since each node in a tree has a unique rooted path (e.g. `rPa` and `rPd`), an
additional extension can not add any edge (e.g. `dEa`) that connects an ancestor
with a descendant. That is because a path `aPd` can then be formed that connects
an ancestor with its descendant.

Note that, since the embedding of a child order will turn any presequent
sibling of a node into an ancestor of that node, and thus into an element
of the node's extended rooted path, valid future embeddings will also be
order maintaining in regards to an embedded child order.

Because of that, if an order embedding is reduced to connecting incomparable
nodes only (which it obviously must be), then the resulting node order will
preserve any pre-existing suborder.

<!-- ======================================================================= -->
## available options

Since a total order has one and only one leaf (i.e. a greatest element), and
since a tree has in general more than one leaf node, the intention of a valid
order embedding is to reduce the amount of incomparable nodes and thus to
ultimately reduce the amount of leaf nodes to one leaf only.

As can be seen due the embedding of a child order, the amount of incomparable
nodes can be reduced by **connecting siblings** with each other. That is, each
edge will reduce the amount of incomparable pairs by one pair only.

Note that the descendants of two child nodes will remain incomparable since the
edge added between them will not allow to form a path between these nodes. That
is because the rooted paths of such descendants are disjoint, meaning that one
will still first have to travel against the orientation of the edges up towards
one of the newly connected child nodes, and then down towards the descendant of
the other child node. Consequently, one can still not form a valid path between
two such descendants.

Despite that, the embedding of a child order will turn **leaf nodes**, which
are no last child to a parent, into parent nodes. In contrary to that, leaf
nodes which are the last child of a parent will remain leaf nodes in the
resulting tree order.

Note that turning a **last child leaf node** into a parent node by connecting
it with a parent node as its child will establish a path between the leaf and
all the descendants of the target parent. Consequently, such connections will
turn multiple pairs of incomparable nodes into comparable ones. Because of that,
adding connections between a last child leaf and a parent will be the focus of
furter order embeddings.