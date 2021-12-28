
<!-- ======================================================================= -->
# general remarks

<!-- ======================================================================= -->
## relevant previous isomorphisms

**T-Hs** - A tree (T) allows to form a hierarchy of scopes (Hs) such that the
source tree can be recreated based on the relationships between its scopes.
However, such a hierarchy does not embed the child order of a document tree
(DT).

**T-Ht** - A tree (T) also allows to form a hierarchy of induced subtrees (Ht)
such that the source tree can be recreated based on the relationships between
its trees. However, such a hierarchy does also not embed the child order of a
document tree (DT). That is because the trees in Ht are the induced subtrees
over the unordered document tree (DTU).

**DT-Hpre** - In contrary to the above, a document tree (DT) allows to form a
hierarchy of pre-order traces (Hpre) such that the source tree, including its
child order, can be recreated based on the relationships between its traces.
That is because the child order is already embedded into the document tree's
trace (i.e. the trace of its root) and also (partially) into the traces of
every induced subtree over DTU.

<!-- ======================================================================= -->
## order-preserving traces

Recall that the **pre-order** tree traversal is order-preserving, which is
why the document tree's child order is a suborder to the doctree's pre-order
trace. After all, the pre-order trace of a tree can be described as a sequence
of **interleaved child orders**.

Recall that the **level-order** tree traversal is order preserving, which is
why the document tree's child order is a suborder to the doctree's level-order
trace. After all, the level-order trace of a tree can be described as a sequence
of **subsequent child orders**.

Recall that, even though the **post-order** tree traversal is *not* overall
order-preserving since it does not maintain the tree order (i.e. ancestor-of).
However, a post-order traversal is still order-preserving in regards to the
child order of a document tree. After all, even the post-order trace of a
tree can be described as a sequence of **interleaved child orders**.

Recall that the **reversed pre-order** and the **reversed post-order** tree
traversal algorithms visit the child nodes of a parent from its last to its
first child. That is, the traces of these tree algorithms do not embed a
doctree's child order. However, one can still derive the child order of a
parent, if the order one can derive is reversed as a last processing step.
