
# abstract properties (2)

build upon the use of abstract properties
- in the context of ordered sequences (total orders)
- in the context of node trees (partial orders)

<!-- ======================================================================= -->
## first - types of scopes

introduce the term "type x scope of node y"
- based upon the corresponding node order

introduce the term "type-x descendants"?
- based on the definition of "types of scopes"
- instead of "the descendants in the the un-ordered tree"
- a descendant in regards to the type-x node order

the general pattern of defining scopes
- also applies to total orders
- type-0 - no edges have been added
- type-1 - the edges of the order
- the resulting order is total
- no more types possible

<!-- ======================================================================= -->
## next

allow overlapping scopes?
- no - induced subtrees do not overlap each other
- related in a path graph
- disjoint exor related in a tree

gaps in a trace
- depens on the linear extension?
- pre- vs. post-order vs. other
- post-order is not order-preserving
- does not work with abstract properties

<!-- ======================================================================= -->
## in the end

some-of as a composed quantifier
- relevant beginning with partial orders
- some-of := all-of, but none-of
- an interval-based point of view
- some-of := (a,*) \ (b,*)
