
# tree traversal (2)
- forming traces of nodes from an ordered doctree

Note that, since the last node of a sequence of siblings will be connected with
a parent node, in-order tree traversals won't be the focus of this discussion.
That is because such a tree traversal requires a node to be visited in between
its child nodes. After all, the traversal trace is not order preserving since
a node would then be subsequent to its first child.
