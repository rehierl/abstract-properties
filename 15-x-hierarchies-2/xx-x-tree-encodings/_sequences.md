
- sequence-base tree encodings

from a sequences to orders
- elements will have to be repeated in order to define
  non-linar orders using sequences
- a sequence can thus only define the structure, it can
  not hold the elements itself - provided externally
- consequently, references of some sort are required to
  map elements onto the structure that is defined
- using unique id/index values as the elements of that
  sequence has the same issue as directly storing the
  elements themselves inside of the remaining sequence
- no other choice but to use the index of each component
  as a reference to the corresponding element
- which leaves the question - what can the values of
  the components be used for?
- since each component can hold one value only,
  there is only one way to directly encode a hierarchy
- the value of each component holds the index of the
  element that is supposed to be the parent node
- the root's parent must have index 0 - as the only
  non-valid index-based reference allowed
- as such, a sequence can be used to more-or-less
  directly define a forest of trees

sequences can be used to define trees
- direct edges - (f: Index -> Index)
- (a,b) = (a child-of b)
- child-of, not parent-of (!)

sequences can be used to define trees (?)
- nested intervals - (f: Index -> Length)
- (a,b) = the pre-order trace of (a) has length (b)
- i.e. stretches over the next (b) nodes
- i.e. a length-based encoding

sequences can be used to define trees (?)
- node level/depth - (f: Index -> Depth)
- (a,b) = node (a) is at node level (b)
- i.e. a depth-based encoding
- seems to allow to derive a length-based encoding
