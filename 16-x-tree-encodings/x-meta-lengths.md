
Hlen
- a hierarchy of length values

todo, about
- show the corresponence between
  a hierarchy of traces and
  a sequence of length values

an in-order tree traversal
- visits a node multiple times
- e.g. count the descendants

pre-order
- in regards to streaming large documents
- expands the distance between a node and its next sibling
- which increases the total number of descendants
- not accurate - there may be descendants behind a last child

sequences can be used to define trees (?)
- nested intervals - (f: Index -> Length)
- (a,b) = the pre-order trace of (a) has length (b)
- i.e. stretches over the next (b) nodes
- i.e. a length-based encoding
