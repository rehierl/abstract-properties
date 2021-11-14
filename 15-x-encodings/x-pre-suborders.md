
<!-- ======================================================================= -->
## sub-orders to a pre-order trace

Recall that each pre-order trace is an ordered sequence of nodes. Because of
that, the pre-order trace of a tree corresponds with a total node order. And
since each scope over a base order is a substring to the doctree's pre-order
trace, each scope can be said to correspond with a total suborder to the
doctree's pre-order trace.

Furthermore, since the pre-order trace of a node (i.e. its type-1 scope) is a
substring to the traces of its ancestors, the pre-order trace of each node is
a total suborder to the trace of the tree's root.

Similar to that, the partial order of an unordered tree is embedded into the
total order of its pre-order trace. (Recall that a visualization is the cover
graph of a tree's node order - i.e. only its transitive reduction is visible).

Likewise, and because the child order of each parent node is embedded into
a pre-order trace, the partial order of the ordered tree is also a sub-order
to a pre-order trace. Because of that, each rooted path in both trees is a
total sub-order to a pre-order trace.

Due to the above, each pre-order trace can be understood to have several
**total and partial sub-orders** embedded into it. All the edges of all
these sub-orders are therefore **consistently oriented** (i.e. oriented
towards the last node of a tree's pre-order trace).

The pre-order trace of a tree therefore has the following sub-orders:

* the scope of each property
* the pre-order trace of each node
* the partial order of the un-ordered tree
* all the child orders
* the partial order of the ordered tree
* all the rooted paths
* all the edges in each sub-order
