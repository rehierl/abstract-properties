
<!-- ======================================================================= -->
# breadth-first search (BFS), level order

A tree traversal is referred to as a breadth-first search (BFS), if the nodes
in a tree are visited one node level at a time.

```js
//- the default level-order tree traversal
traverseBFS(root) {
  next = new Queue();
  next.enqueue(root);

  while (next.isEmpty() == false) {
    node = next.dequeue();
    visit(node);

    for (child in node.childNodes) {
      next.enqueue(child);
    }
  }
}
```

Note that the above pseudocode defines what is commonly known as
**the (default) level-order tree traversal**.

Note that the default level-order tree traversal will visit the nodes in tree
order (ancestors before descendants) and also according to the tree's child
order (if one exists). Because of that, the (default) level-order traversal
is **order preserving**.

Note that the nodes of a level (i.e. the child nodes of the previous level)
**can in general be visited in random order**. However, as a matter of
simiplification one will in general first visit all the child nodes in
first-to-last order. Because of that, variations will in general visit the
child nodes of a parent in some other order.

Note that the level-order tree traversal **can be restricted** to only visit
the nodes within the first couple of node levels.
