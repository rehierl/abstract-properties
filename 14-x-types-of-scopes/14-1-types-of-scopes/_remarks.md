
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

point out that there are no overlapping scopes
- guaranteed by construction
- related in a path graph
- disjoint exor related in a tree

well defined sets of edges
- base orders have a formal definition
- the pre-order trace has a formal definition
- scopes defined over a known base order have a formal definition
- even if that definition is not intuitive to everyone

# remarks

all exor none
- can a suborder end with a parent, but exclude its child nodes?
- either includes a node and all of its descendants, exor none at all
- needs substring-based considerations

possibly slightly different to ..
- a scope includes a node and all of its descendants ex-or none at all
- which still needs to be confirmed or dismissed.

# meta / beyond

even a total base order allows to define a hierarchy
- `scope(x) := [x,*] \ [y,*]`

the general pattern of defining scopes
- also applies to total orders
- type-0 - no edges have been added
- type-1 - the edges of the order
- the resulting order is total
- no more types possible
