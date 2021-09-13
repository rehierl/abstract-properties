
some-of as a composed quantifier
- relevant beginning with partial orders
- some-of := all-of, but none-of
- an interval-based point of view
- some-of := (a,*) \ (b,*)

an end tag, some-of
- does not just mark the end of a type-1 scope
- it also divides a type-2 scope into two branches
- left of it are the descendants of the tag's node, and to
  the right are the subsequent siblings and their descendants
- an end-tag separates a node's type-1 (t1)
  descendants from its remaining t2 descendants
- a partition of its type-2 descendants
- an end-tag provides a clear definition
  for the some-but-not-all quantifier

<!-- ======================================================================= -->
# remarks

define/identify the last node of a scope

* A scope's first node can be identified with ease (e.g. via attributes).
  As such, a first node will be referred to as the scope's defining node.
* The pre-order trace of a tree embeds several total and partial sub-orders.
* The defining node of a scope is expected to be the first node of such a
  well-defined sub-order. That is because it must be possible to uniquely
  identify the corresponding sub-order as soon as a first node is reached.
* The last node of a scope can be defined as the last node of a sub-order,
  which enables implementations to determine the last node of a scope
  based on these nodes having no outgoing edge.
