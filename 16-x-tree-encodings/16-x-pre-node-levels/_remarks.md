
Hlvl
- a herarchy of level values (lvl-rps)
- a level-based encoding

todo, about
- show the correspondence between
  a sequence of length values and
  a sequence of level values
- note - level values are equivalent
  to rank values

a hierarchy of rooted paths
- needs an index-based setup of rooted paths
- could result in a level-based encoding
- `level(n) := #rp(n)` - the node level of a node
- allows for a non-tag based notation
- the node levels act as rank values
- in essence a sequence of rank values
- requires a pre-order trace of paths/scopes

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- i.e. while deserializing a tree, `#s`
  tells where to place the next element
- i.e. the element's node-level value

level values vs. rank values
- level values count the number of traces/scopes
- level values can be read as instructions
  to end/close the corresponding scopes
- not any different to rank values
- if generated, they can be relied upon
- level values are absolute

question ?!?
- is there a transition from DI-RE to RE-OV
-

a generalized point-of-view
- level values allow to form groups of elements
- which is common to the topic of sections
