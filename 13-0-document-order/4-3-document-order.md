
<!-- ======================================================================= -->
# the document order

Recall the prologue and chapter 05, which introduced **the document order** as
a total node order over all the nodes in a document tree. More accurately, the
document order must be understood **a processing order** that is needed in
order to guarantee consistent results across all implementations.

Recall that **the pre-order and the level-order tree traversal algorithms**
are the only **overall order preserving** tree traversal algorithms. That is,
both algorithms visit the nodes in tree order and also in child order.

Since the level-order trace of a tree can be described as a sequence of disjoint
child orders, and since that trace is as such non-hierarchical, one can conclude
that the document order can not be in level order. Consequently, the document
order can already be concluded to be **in pre-order**.

Recall that the pre-order trace of a tree is a hierarchical ordered sequence
of nodes. That is because **the scope of each node appears a substring** such
that all the scopes are either disjoint ex-or related (**DI-RE**).

Recall that the trace of a node is a substring to the traces of its ancestors,
a pre-order trace, including the trace of a document tree, can be described
as a sequence of **interleaved child orders**.

<!-- ======================================================================= -->
## the document order is the total pre-order

Recall that **the above-of node order** (as outlined in the prologue) was
introduced as a reference to the document order. With that in mind, the
following statements are true.

* The doctree's pre-order traversal defines the doctree's pre-order node order.
* The tag soup of a document encodes the doctree's pre-order node order.
* **The total document order is equivalent to the pre-order node order**.
* The tag soup of a document encodes a hierarchy of scopes.
* The tag soup of a document is isomorphic to the document tree.
* **The document tree is a partial suborder to the document order**.

In regards to the document tree's pre-order trace, the above-of node order
must be understood to be defined based on the doctree's pre-order trace.

* `(a above-of b) := (a presequent-to b)`

And there shouldn't even be the slightest shred of doubt about that!

<!-- ======================================================================= -->
## remarks

Recall that no node above-of a heading belongs to a heading's section. Because
of that, no node can count towards the section of a heading, if the heading is
subsequent to that node in the document tree's pre-order trace. That is, a node
can not be associated with the section of a heading, if the node is an ancestor
of that heading, a presequent sibling of that heading (or one of the descendants
of such a node), or a presequent sibling of one of the heading's ancestors (or
one of the descendants of such a sibling).

Conversely, the subsequent siblings of a heading (including their descendants),
the subsequent siblings of the heading's ancestors (including their descendants)
are subsequent to that heading in the document tree's pre-order trace. Because
of that, all of these nodes may in principle be content nodes in the section of
a heading.

Recall however that the document order does by itself not allow to conclude,
if specific nodes that are subsequent to a heading in the document order, are
indeed content nodes in the section if a heading. Further defintions are thus
required.
