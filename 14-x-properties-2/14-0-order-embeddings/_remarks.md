
- provide visual examples for order embeddings
- detailed explanations with visual examples
- i.e. how node orders are embedded into other node orders
- note - suborder vs. subgraph/subtree

# total into total

- e.g. child orders, rooted paths
- the rooted path rpU(n) in the unordered doctree
- rpU(n) is unequal to rpO(n)
- rpU(n) is no prefix to rpO(n)
- rpU(n) is a suborder to rpO(n)

# total into partial

- each edge in a tree is an embedded total suborder
- each rooted path in a tree is an embedded total suborder
- each child order is a path/subtree to an ordered doctree
- each child order is an embedded total suborder to an ordered doctree

# partial into total

- e.g. a tree in a pre-order trace
- not embedded as a subtree

# partial into partial

- an unordered doctree is no subtree to an ordered doctree
- an unordered doctree is still a suborder to an ordered doctree
- e.g. connected via an incoming border edge
- e.g. an unordered tree in its ordered tree
- the partial order relation is not embedded as a subtree
- e.g. the section hierarchy?
- defined by, but not embedded as a suborder

# no embedding

- the pre-order trace of a doctree is not embedded into the doctree
- has edges that are no edges in the ordered doctree
- doh .. the trace is total, the doctree is not
- we use partial orders to process/visualize a document
- vs. we use total orders to define a document
- a tag soup defines a total order, embeds a partial order
