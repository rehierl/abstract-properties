
- sequence-based tree encodings
- howto store non-linear orders using sequences

from a sequences to orders
- in order to correspond with non-linear orders,
  sequences must hold elements repeatedly
- in regards to non-linear orders, a sequence can
  only define the structure, but not the actual
  elements - aka. the nodes/vertices in the order
- these nodes must be provided externally
- that is, the elements in a sequence can only be
  used to define the non-linear structure

references
- references of some sort can be used to map the
  elements onto the structure that is defined
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

grouping
- using group-ids as the elements in a sequence
  allows to group the actual elements, which
  can be identified by the corresponding index

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
