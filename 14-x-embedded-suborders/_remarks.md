
- show examples for order embeddings
- justify and introduce types of scopes

# meta / later

sequences of subsequent siblings
- in the ordered doctree
- s(n) is a suffix to s(p)
- c(n) is disjoint-to c(p)
- where (p parent-of n) is true

total orders embedded into total orders
- the rooted path rpU(n) in the unordered doctree
- rpU(n) is unequal to rpO(n)
- rpU(n) is no prefix to rpO(n)
- rpU(n) is a suborder to rpO(n)

total orders embedded into partial orders
- each edge in a tree is an embedded total suborder
- each rooted path in a tree is an embedded total suborder
- each child order is a path/subtree to an ordered doctree
- each child order is an embedded total suborder to an ordered doctree

partial orders embedded into partial orders
- an unordered doctree is no subtree to an ordered doctree
- an unordered doctree is still a suborder to an ordered doctree

# beyond

when to associate (2)
- in regards to the node order of an ordered doctree
- needs box-based visuals to understand properly
- a subsequent sibling may belong to the property of a presequent sibling
- a presequent sibling can not belong to the property of a subsequent sibling
- the transition towards context based on rooted paths
- a property applies to all the descendants in the corresponding suborder
- suborders may in general end at any point
- even before reaching a certain end-tag
- associate while exiting - a formal design error
