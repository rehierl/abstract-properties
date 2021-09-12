
# abstract properties (2)

build upon the use of abstract properties
- in the context of ordered sequences (total orders)
- in the context of node trees (partial orders)

allow overlapping scopes?
- why, types of properties have no overlapping scopes
- so why allow such scopes in the context of sections?

with which properties to associate
- will require a definition of "context"
- will require the definition of types of scopes
- in regards to the node order of an ordered doctree
- needs box-based visuals to understand properly
- a subsequent sibling may belong to the property of a presequent sibling
- a presequent sibling can not belong to the property of a subsequent sibling
- the transition towards context based on rooted paths
- a property applies to all the descendants in the corresponding suborder
- suborders may in general end at any point
- even before reaching a certain end-tag
- associate while exiting - a formal design error
