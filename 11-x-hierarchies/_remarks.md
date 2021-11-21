
a hierarchy of rooted paths
- needs an index-based setup of rooted paths
- could result in a level-based encoding
- level, not depth .. depth(r)=0, level(r)=1
- allows for a non-tag based notation
  i.e. each node has a rank .. its node level
- in essence a sequence of rank values
- requires a pre-order trace of paths/scopes

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- i.e. while deserializing a tree, `#s`
  tells where to place the next element
- i.e. the element's node-level value

a hierarchy of things
- as a note in a readme/summary
- is itself not required to be hierarchical
- e.g. a hierarchy of rooted paths, edges
- a hierarchy must embed the definition of a tree
- i.e. a hierarchy must correspond with a tree

the universal set/graph issue
- figure out what the general case is
- pick one and drop the other
