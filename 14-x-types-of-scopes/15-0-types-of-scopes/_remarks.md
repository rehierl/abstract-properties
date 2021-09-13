
- do actually define types of scopes/properties
- the document order is the doctree's pre-order trace
- derived from that - types of properties/scopes
- this is in essence about "naming orders"

introduce the term "type x scope of node y"
- based upon the corresponding node order

introduce the term "type-x descendants"
- based on the definition of "types of scopes"
- instead of "the descendants in the the un-ordered tree"
- a descendant in regards to the type-x node order

recall - each scope is an interval
- a property applies to all the nodes
  that are subsequent to its defining node
- now the question is .. according to which node order ?!?
- rooted paths - according to which node order ?!?

point out that there are no overlapping scopes
- guaranteed by construction
- related in a path graph
- disjoint exor related in a tree

# meta / beyond

the general pattern of defining scopes
- also applies to total orders
- type-0 - no edges have been added
- type-1 - the edges of the order
- the resulting order is total
- no more types possible

<!-- ======================================================================= -->
# remarks

Note that, since a pre-order trace is an ordered sequence of nodes, no node in
a pre-order trace appears more than once. Because of that, each property can
be understood to have a well defined **offset** (i.e. the index of its defining
node) in the trace of a tree. Based on that, **relationships** between distinct
properties can be defined in terms of an order of appearance (i.e. in regards
to their offsets).
