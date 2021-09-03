
# tree traversal

- treat a node trace as a super-sequence of interleaved
  (traces of nodes) and overlapping sub-sequences (rooted paths)
- vertical orders (i.e. rps) and horizontal orders (i.e. child orders)

remarks
- add the pre-order edges to the tree order of the ordered tree
- this will result in the pre-order trace of nodes
- referred to as a (linear) extension of the tree order
- explain the inner structure of the pre-order trace

pre-order is dominant
- child orders are sub-orders
- the reason why preorder is dominant
- order preserving in regards to all
  of the embedded suborders
- including any child order

level-order traversal
- also in pre-order
- however, a node and its child nodes
  are anyhting but in close proximity

an embedding consists of an ordering rule and an order of execution
- rule - how a sequence is formed - additional edges
- execution - in which order these rules must be applied
- in regards to the overall serialization ?
- i.e. child order, then pre-order

# meta

sequence of siblings
- the goal find a more generic term for a sequence
  of things that have some characteristic in common
- e.g. a sequence of peers - "peer" is less common but still already in use

an issue with "sequences of siblings"
- synonymous to a particular "child order"
- is that description too confusing?
- still seems to provide a connection to what we know
- i.e. based on current experiences
- "siblings" in regards to distinct elements
  that share some common aspect - a (former) parent node
- so "sequences of siblings" is not to be misunderstood
  in regards to specific siblings within a node tree
- more general - synonymous to "ordered sequences"
