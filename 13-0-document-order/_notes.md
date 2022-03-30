
- the definition of document order
- when to associate
- html elements

<!-- ======================================================================= -->
## conclusions

- a tag soup is bound to the default pre-order traversal of a document tree
- `(n × <tag> × c × </tag> × s)` => `(<n attribute*> × c × </n> × s)`
- the document order is the pre-order node order

Note that the edges defined by the pre-order rule are not embedded into the
document tree. That is, according to a document tree, a child is not presequent
to any of the subsequent siblings of its ancestors. In other words, the next
subsequent sibling of a node is not subsequent to any of its descendants.

- when to associate
- no ancestor is within the scope of a descendants
Note that, since the start-tag of a node can be understood to define a node
and also its absolute position in the document order, and since the document
order is in pre-order, no ancestor of a node is subsequent to any of its
descendants. Because of that, no ancestor can belong to any property that is
defined by any of its descendants.

<!-- ======================================================================= -->
## remarks

Since each node can be understood to be pushed into its start-tag, a start-tag
can be said to correspond with the visit of a node. The start-tag of a node
can therefore be understood such that it **defines the absolute position**
of a node and therefore to **denote the start of the node's scope**.

* start-tag => enter the scope of a node and visit that node

Note that, since each start-tag can be understood to correspond with a
node in the document tree that has a unique position associated with it,
a document tree can be described as **an ordered tree** in the sense of
**a tree of unique/distinct elements** which is associated with a tree order.
That is, the description of "an ordered treee" should be understood in the
sense of "an ordered sequence of distinct elements", not in the sense that
it has a child order!

Note that, in contrary to the above, the subsequence of all end-tags reflects
**the exit-order**. That is, an end-tag does not correspond with the visit
of any node since **an end-tag only marks the end of a scope**.

* end-tag => only exit the node's scope

<!-- ======================================================================= -->
## readme

From an input-based point of view, **the tag soup of a document** can be
understood to define the document tree's pre-order trace - with the additional
feature that there is an end-marker for the scope of each node.

- the enter-order corresponds with the (pre-order) visit order
- each start-tag corresponds with the visit of a node
- each start-tag denotes the absolute position of a node
- each start-tag defines the corresponding node via its attributes
- each start-tag denotes the start of the node's scope
- an end-tag (only) denotes the end of the node's (type-1) scope
- an end-tag does not correspond with any node

Based on how the tag soup of a document is formed from its document tree,
one can conclude that **a tag soup ain't no node tree**.

- a tag soup does not directly define any edges
- a tag soup directly encodes a hierarchy of scopes instead
- a tag soup does not define a node tree, but a containment order
- a tag soup embeds the document tree's pre-order node order
- the document tree's tree order is a partial suborder
