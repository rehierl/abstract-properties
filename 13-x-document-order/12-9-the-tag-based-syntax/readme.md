
# document order / the tag-based syntax

tag soup
- produced by combining the pre-order and the post-order tree traversal
- a tag soup can be seen as a sequence of enter- and exit-events
- each enter-event is paired with a subsequent exit-event

pre-order traversal
- the enter-order corresponds with the pre-order visit order
- each start-tag corresponds with the visit of a node
- each start-tag denotes the absolute position of a node
- each start-tag defines the corresponding node
- the document order is equivalent to the pre-order node order
- each start-tag also denotes the start of the node's scope
- in contrary to that, an end-tag does not correspond with any node
- an end-tag (only) denotes the end of the node's (type-1) scope

* start-tag <=> enter a node's scope and visit that node
* end-tag <=> only exit the node's scope

a tag soup ain't no node tree
- a tag soup encodes the doctree's pre-order node order
- a tag soup directly encodes a hierarchy of scopes
- a tag soup does not define a node tree, but a containment order
- the tree order is a partial suborder to the document order

Note that, since the start-tag of a node can be understood to define a node
and also its absolute position in the document order, and since the document
order is in pre-order, no ancestor of a node is subsequent to any of its
descendants. Because of that, no ancestor can belong to any property that is
defined by any of its descendants.
