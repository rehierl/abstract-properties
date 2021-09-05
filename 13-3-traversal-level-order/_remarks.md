
# level-order traversal

the level-order rule is somewhat incomplete
- one must define in which order the child orders must be appended
- the level-order rule must therefore be missing some edges
- why exactly is that the case?

# tree encoding - by level

the level-order trace
- does not correspond with a hierarchy of substrings
- a concatenation of disjoint child orders

ordered sequences define trees
- the parent reference of each node
- can be understood as a shared property
- which groups the child nodes of a parent
- the level-order trace is a specialized encoding
