
- the document order is the doctree's pre-order trace
- derived from that - types of properties/scopes
- this in essence about "naming orders"

recall - a scope is an interval
- a property applies to all the nodes
  that are subsequent to its defining node
- now the question .. according to which node order ?!?
- rooted paths - which node order ?!?

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

the extension of scopes
- type-0 is "only the node"
- type-1 is "the scope of a node"
- all descendants in the unordered doctree
- type-2 is "the extended scope of a node"
- all descendants in the ordered doctree
- its descendants + siblings and their descendants
- show - a sequence of units - induced subtrees
- similar boxing issues with distant descendants
- restricted by the scope of their parent
- type-3 is "the unrestricted scope of a node"
- until the very end of a document
