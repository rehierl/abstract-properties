
<!-- ======================================================================= -->
## sub-orders to a pre-order trace

Recall that each pre-order trace is an ordered sequence of nodes. As such,
the pre-order trace of a tree corresponds with a total node order. And since
each scope over a base order is a substring to the doctree's pre-order trace,
each scope can be said to correspond with a total suborder to the doctree's
pre-order trace.

Furthermore, since the pre-order trace of a node is a substring to the traces
of its ancestors, the pre-order trace of each node is a total suborder to the
trace of the doctree's root.

Similar to that, the partial order of an unordered doctree is embedded into
the total order of its pre-order trace. (Recall that the visualization as a
node tree is a mere cover graph of a tree's node order. That is, only its
transitive reduction is visualized).

Likewise, and because the child order of each parent is embedded into the
pre-order trace of a doctree, the partial order of the ordered doctree is
a sub-order to the doctree's pre-order trace. Because of that, each rooted
path in both trees is a total sub-order to the doctree's pre-order trace.

Due to the above, each pre-order trace can be understood to have several
**total and partial sub-orders** embedded into it. That is, the edges of
all of these sub-orders are **consistently oriented** (i.e. oriented
towards the last node of the doctree's pre-order trace).

The pre-order trace of a tree therefore has the following sub-orders:

* the pre-order trace of each node
* the partial order of the un-ordered doctree
* the child order of each parent
* the child order of the document tree
* the partial order of the ordered doctree
* the rooted path of each node
* all the edges in each sub-order

Note that, like the child order of each parent, the rooted paths over all base
orders are total sub-orders to the pre-order trace of a document tree.

Note that the scope of a property over any base order appears as a substring to
the doctree's pre-order trace. Based on that, the scope of any property can be
understood to correspond with one or more suborders to the doctree's pre-order
trace - a suborder to the base order, and a substring to the pre-order trace.
