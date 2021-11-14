
a hierarchy of rooted paths
- is such that RE-OV - rooted paths
- is a hierarchy of trees

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
- i.e. during the deserializing a tree,
  `#s` tells where to place the next element
- i.e. the element's node-level value
