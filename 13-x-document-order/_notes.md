
## the tag-based syntax

From an input-based point of view, the tag soup of a document can be understood
to define the document tree's pre-order trace - with the additional feature
that there is an end-marker for the scope of each node.

- the enter-order corresponds with the (pre-order) visit order
- each start-tag corresponds with the visit of a node
- each start-tag denotes the absolute position of a node
- each start-tag defines the corresponding node via its attributes
- each start-tag denotes the start of the node's scope
- an end-tag (only) denotes the end of the node's (type-1) scope
- an end-tag does not correspond with any node

## conclusions

- a tag soup is bound to the default pre-order traversal of a document tree
- `(n × <tag> × c × </tag> × s)` => `(<n attribute*> × c × </n> × s)`
- the document order is the pre-order node order

a tag soup ain't no node tree
- a tag soup encodes the doctree's pre-order node order
- a tag soup directly encodes a hierarchy of scopes
- a tag soup does not define a node tree, but a containment order
- the tree order is a partial suborder to the document order

Note that the edges defined by the pre-order rule are not embedded into the
document tree. That is, according to a document tree, a child is not presequent
to any subsequent sibling of its parent. In other words, the next subsequent
sibling of a node is not subsequent to any of its descendants.

- no ancestor is within the scope of a descendants
Note that, since the start-tag of a node can be understood to define a node
and also its absolute position in the document order, and since the document
order is in pre-order, no ancestor of a node is subsequent to any of its
descendants. Because of that, no ancestor can belong to any property that is
defined by any of its descendants.
