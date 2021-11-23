
# level-based encoding

a hierarchy of rooted paths
- needs an index-based setup of rooted paths
- could result in a level-based encoding
- level(n) := #rp(n)
- allows for a non-tag based notation
- the node levels act as rank values
- in essence a sequence of rank values
- requires a pre-order trace of paths/scopes

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- i.e. while deserializing a tree, `#s`
  tells where to place the next element
- i.e. the element's node-level value
