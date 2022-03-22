
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

```js
//- the default pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the current node
  visit(node);

  //- visit the node's child nodes
  for(child in node.childNodes) {
    traverseInPreOrder(child);
  }
}
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
set of elements, whereas the latter is in regards to an order relation.

<!-- ======================================================================= -->
## post-order tree traversal

```js
//- the default post-order tree traversal
traverseInPostOrder(node) {
  //- visit the node's child nodes
  for(child in node.childNodes) {
    traverseInPostOrder(child);
  }

  //- visit the current node
  visit(node);
}
```

The (default) post-order tree traversal will visit a node after all of its
descendant nodes have been be visited. Hence, the description as post-order
(i.e. "post-" as in "last").

Note that the (default) post-order tree traversal will *not* visit the nodes
in tree order (ancestors before descendants). That is because the descendants
of a node will be visited before the node is being visited. Consequently, and
even though the child order (if one exists) is preserved, the overall tree
traversal is **not order preserving**.

<!-- ======================================================================= -->
## in-order tree traversal

```js
//- the default in-order tree traversal
traverseInOrder(node) {
  //- visit the 1st child
  visit(node.leftChild);

  //- visit the current node
  visit(node);

  //- visit the 2nd child
  visit(node.rightChild);
}
```

The (default) in-order tree traversal in general only applies to binary trees
(two child nodes only). It will visit a node after its 1st has been visited
and before its 2nd child will be visited. Hence, the description as in-order
(i.e. "in-" as in "in between").

Note that the (default) in-order tree traversal will not visit the nodes in
tree order (ancestors before descendants). That is because a node's first child
will be visited before a node itself will be visited. Consequently, and even
though the child order (if one exists) is preserved, the overall tree traversal
is **not order preserving**.

```js
//- the default in-order tree traversal
traverseInOrder(node)
  for(child in node.childNodes) {
    //- before each child
    //- visit the current node
    visit(node);

    //- visit the current child
    traverseInOrder(child);

    //- after each child
    //- visit the current node
    visit(node);
  }
}
```

Note that variations are possible which allow to traverse generic trees (any
number of child nodes) using an in-order traversal. However, such non-strict
variations will visit nodes more than once and are therefore not in the focus
of this discussion.
