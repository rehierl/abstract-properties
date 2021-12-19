
- each entry in a sequence is the index of another element
- a direct/explicit encoding - i.e. no compression
- no other choice but to use the index of each component
  as a reference to the corresponding element
- the value of each component holds the index of the
  element that is supposed to be the parent node
- the root's parent must have index 0 - as the only
  non-valid index-based reference allowed
- as such, a sequence can also be used to encode a forest

implicit encodings
- e.g. in terms of level values or scope sizes

sequences can be used to define paths
- direct edges - (f: Index -> Index)
- (a,b) = (a parent-of b)
- can not support general trees

sequences can be used to define trees
- direct edges - (f: Index -> Index)
- (a,b) = (a child-of b)
- child-of, not parent-of (!)

grouping
- using group-ids as the elements in a sequence
  allows to group the actual elements, which
  can be identified by the corresponding index

sequences can be used to define trees (?)
- nested intervals - (f: Index -> Length)
- (a,b) = the pre-order trace of (a) has length (b)
- i.e. stretches over the next (b) nodes
- i.e. a length-based encoding

sequences can be used to define trees (?)
- node level/depth - (f: Index -> Level)
- (a,b) = node (a) is at node level (b)
- i.e. a level-based encoding
