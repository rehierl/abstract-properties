
<!-- ======================================================================= -->
# examples of suborders

The following will provide general examples of notable suborders.

Note that not every suborder is an actual subgraph to the cover relation of a
super-order. In contrary to that, and in the context of this discussion, each
subgraph (e.g. induced subtrees) corresponds with an actual suborder.

Note that the following examples will in general describe the default case,
while ignoring special edge cases which have the potential to render those
statements invalid that are attached to the following examples.

<!-- ======================================================================= -->
## total suborders to total orders

(*) A substring `s` to an ordered sequence `S` corresponds with a path in
the path graph of `S`. Because of that, `s` is also a total suborder to `S`.

(*) The rooted path of a node in the unordered doctree `rpU(n)` is no path to
the rooted path of that node in the ordered doctree `rpO(n)`. However, `rpU(n)`
still corresponds with a total suborder to `rpO(n)`.

(*) The sequence of presequent siblings of a node `s(n) := (fs..ps)` is a path
in the rooted path of that node `rpO(n)` in the ordered doctree. As such, that
sequence of presequent siblings is also a total suborder to that rooted path.

<!-- ======================================================================= -->
## total suborders to parital orders

(*) Each edge in a tree order is a total suborder to the tree order. However,
not each such edge is also an edge in the node tree.

(*) Each rooted path of a node `rp(n)` in a tree is a subgraph of the tree.
In addition to that, the total order of a rooted path is a total suborder to
the tree order of the node tree.

(*) The rooted path of a node in the unordered doctree `rpU(n)` is in general
unequal to the roted path of that node in the ordered doctree `rpO(n)` and as
such no rooted path in that tree. However, `rpU(n)` is still a total suborder
to the tree order of the ordered doctree.

(*) The child order of each node `co(n)` is a path in the ordered doctree.
As such, a child order is a total suborder to the tree order of the ordered
doctree.

<!-- ======================================================================= -->
## partial suborders to total orders

(*) The unordered doctree and the ordered doctree are both proper partial
suborders to the doctree's pre-order trace. However, none is in general a
subtree to the path graph of the pre-order trace.

<!-- ======================================================================= -->
## partial suborders to partial orders

(*) An unordered doctree is no subtree to an ordered doctree. However, an
unordered doctree is still a partial suborder to the ordered doctree.

<!-- ======================================================================= -->
## no order embeddings

(*) The pre-order trace of a doctree is not embedded into the doctree's node
order. That is because that trace contains edges that are neither edges in the
unordered nor edges in the ordered doctree. In addition to that the pre-order
trace of a tree is also no total suborder to these tree orders.

(*) The pre-order trace of a node (i.e. the pre-order trace of its induced
subtree) is neither a suborder to the unordered doctree nor the ordered doctree.
These traces are however still suborders to the doctree's pre-order trace (i.e.
the trace of the doctree's root node).
