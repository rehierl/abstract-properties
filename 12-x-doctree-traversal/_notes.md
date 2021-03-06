
# in general

the embedding of traversal edges consists of ..
- an ordering rule and an order of execution
- the edges that result from applying the pre-/post-/level-order rule
- rule - how a sequence is formed - additional edges
- execution - in which order these rules must be applied

if you know that you have a transitive closure
- (i.e. some endo-relation that is transitive),
- and the order is a partial order (i.e. no cycles),
- then you know that (a) in (a,x) is a characteristic element
- the union of all the reachable vertices formes the scope of (a)
- a way to efficiently determine the transitive reduction?
- howto distinguish a child from some other descendant?

in regards to embedding sets of edges
- a well-defined set of edges such as the
  edges in the child order of a doctree
- i.e. well-defined as in pre-determined
- the pre-order rule does not correspond
  with a well-defined set of edges since
  there is no pre-calulated set of edges
- one can still state that the document
  order is well-defined as a tag soup

# pre-order traversal

an open question
- can the pre-order traversal be expressed
- as iteratively/repeatedly applying a child order?
- gut feeling says yes ..

# level-order traversal

the level-order rule is somewhat incomplete
- one must define in which order the child orders must be appended
- the level-order rule must therefore be missing some edges
- which edges? why exactly is that the case?

the level-order trace
- does not correspond with a hierarchy of substrings
- a concatenation of disjoint child orders

a level-order sequence-based encoding
- a level-order trace is a specialized encoding
- the parent reference of each node
  can be understood as a shared property
  which groups the child nodes of a parent
- a sequence of integers such that each entry
  olds the index of its parent
- the difference - a level-order trace is such
  that the child nodes are grouped together one
  node level at a time
