
<!-- ======================================================================= -->
## The set of outer sets

**CLARIFICATION**
Each outer set contains its defining node.
That is, no node has an empty outer set.
(=> a simple setup).

**CLARIFICATION**
The outer sets of two distinct nodes are either
disjoint ex-or one is a strict subset to the other.
(=> a strict setup).

(1) If node `n1` is an ancestor of `n2`, then any descendant of `n2` is also
a descendant of `n1`. The outer set of `n2` is therefore a subset of the outer
set of `n1`. That is, the outer set of `n2` does not contain any node that is
not also an element of the outer set of `n1`. Hence, the outer set of `n2` is
a simple subset to the outer set of `n1`.

(2) If node `n1` is an ancestor of `n2`, then the outer set of `n1` has `n1`
as an element, but the outer set of `n2` does not. The outer set of an ancestor
always has more elements than the outer set of a descendant. That is, the outer
set of a descendant is a strict subset of the outer set of an ancestor.

(3) If two nodes are unrelated to one another (i.e. none is an ancestor of the
other), then the outer sets of both nodes are disjoint. That is, both sets have
no node in common.

Note that requirement-2 (i.e. "if coupled, then related") of the definition of
a strict setup is fulfilled since (disjoint ex-or strictly related) is true in
the context of a set of outer sets. Because of that, a set of outer sets is a
strict setup.

**CLARIFICATION**
The set of outer sets always has one any only one root set.
(=> a simple hierarchy).

That is because a node tree has by definition exactly one root to which all
other nodes are descendant. Because of that, the outer set of any other node
is a strict subset to the outer set of the tree's root.

**CLARIFICATION**
Each outer set has its defining node as its only CE.
(=> a strict hierarchy).

The inner set of a node is the union of the outer sets of its child nodes. The
defining node is therefore the only node that will remain after subtracting the
inner set of a node (i.e. the set of its descendant nodes).

**CLARIFICATION**
The **set of outer sets** of a tree is **a strict hierarchy of sets**.
