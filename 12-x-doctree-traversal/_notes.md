
- variable, max number of iterations
- an ordered tree is a binary tree

# in general

if you know that you have a transitive closure
- (i.e. some endo-relation that is transitive),
- and the order is a partial order (i.e. no cycles),
- then you know that (a) in (a,x) is a characteristic element
  since there are no backwards oriented edges - no cycles
- the union of all the reachable vertices formes the scope of (a)
- a way to efficiently determine the transitive reduction?
- howto distinguish a child from some distant descendant?
- a distant descendant is subsequent to a child
- i.e. drop all the descendants of a descendant,
  then only the child nodes will remain

# level-order traversal

iterative pov, option-2
- seems to produce traces that are in level-order
- however, not the default level-order trace

the level-order rule is somewhat incomplete
- one must define in which order the child orders must be appended
- the level-order rule must therefore be missing some edges
- which edges? why exactly is that the case?

a level-order sequence-based encoding
- a level-order trace is a specialized encoding
- the parent reference of each node
  can be understood as a shared property
  which groups the child nodes of a parent
- a sequence of integers such that each entry
  holds the index of its parent
- the difference - a level-order trace is such
  that the child nodes are grouped together one
  node level at a time
