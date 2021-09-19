
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

Note that defining the scope of an operation can be said to hide the difficult
to define **some-of** qualifier. After all, an operation is in general not
intended to apply to all the nodes in a tree.
