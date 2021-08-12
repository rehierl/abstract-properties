
<!-- ======================================================================= -->
# depth-first search (DFS) tree traversal

A tree traversal is referred to as depth-first search (DFS), if the descendants
of a node will be visited before any further sibiling of that node will be
visited.

Note that in general, several variations of the following traversal algorithms
are possible. The most common variation is to simply reverse the child order,
if one is available.

<!-- ======================================================================= -->
## pre-order tree traversal

```
//- the default pre-order traversal
traverseInPreOrder(node) begin
  visit(node)
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end
end
```

The (default) pre-order tree traversal will visit a node before any of its
descendant nodes will be visited. Hence, the description as pre-order (i.e.
"pre-" as in "first").

Note that the (default) pre-order tree traversal will visit the nodes in tree
order (ancestors before descendants) and also according to the tree's child
order (if one exists). Because of that, the (default) pre-order tree traversal
is **order preserving**.

Note that "a pre-order tree traversal" must not be confused with "the preorder
of an ordered set of elements". The former does not define an actual ordered
set of elements, whereas the latter is in regards to a reflexive transitive
order relation.

<!-- ======================================================================= -->
## post-order tree traversal

```
//- the default post-order traversal
traverseInPostOrder(node) begin
  for(child in node.childNodes) begin
    traverseInPostOrder(child)
  end
  visit(node)
end
```

The (default) post-order tree traversal will visit a node after all of its
descendant nodes have been be visited. Hence, the description as post-order
(i.e. "post-" as in "last").

Note that the (default) post-order tree traversal will not visit the nodes in
tree order (ancestors before descendants). That is because the descendants of
a node will be visited before the node is being visited. Consequently, and
even though the child order (if one exists) is preserved, the overall tree
traversal is **not order preserving**.

<!-- ======================================================================= -->
## in-order tree traversal

```
//- the default in-order traversal
traverseInOrder(node) begin
  visit(node.leftChild)
  visit(node)
  visit(node.rightChild)
end
```

The (default) in-order tree traversal in general applies only to binary trees
(two child nodes only). It will visit a node after its 1st has been visited
and before its 2nd child will be visited. Hence, the description as in-order
(i.e. "in-" as in "in between").

Note that the (default) in-order tree traversal will not visit the nodes in
tree order (ancestors before descendants). That is because a node's first
child will be visited before a node itself will be visited. Consequently,
and even though the child order (if one exists) is preserved, the overall
tree traversal is **not order preserving**.

```
//- a modified in-order traversal
traverseInOrderMod(node) begin
  for(child in node.childNodes) begin
    visit(node)
    traverseInOrderMod(child)
  end
end
```

Note that variations are possible which allow to traverse generic trees (any
number of child nodes) using an in-order traversal. However, such non-strict
variations will visit nodes more than once and are therefore not in the focus
of this discussion.
