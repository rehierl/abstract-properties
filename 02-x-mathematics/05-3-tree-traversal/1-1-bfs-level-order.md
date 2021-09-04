
<!-- ======================================================================= -->
# breadth-first search (BFS), level order

A tree traversal is referred to as a breadth-first search (BFS), if the nodes
within a tree are visited one node level at a time, and beginning with the
specified root node.

```
//- the default level-order tree traversal
traverseBFS(root) begin
  queue = new Queue()
  queue.enqueue(root)

  while (not queue.isEmpty) begin
    node = queue.dequeue()
    visit(node)

    for (child in node.childNodes) begin
      queue.enqueue(child)
    end
  end
end
```

Note that the above pseudocode defines what is commonly known as
**the (default) level-order tree traversal**.

Note that all the nodes of a level (i.e. the child ondes of the previous level)
can be visited in any order. However, due to implementation-specific issues
variations will in general first visit all the child nodes of a parent before
visiting the child nodes of another parent. Because of that, variations will
in general visit the child nodes of a parent in some order that deviates from
the parent's child order.

Note also, the level-order tree traversal can in principle be restricted to
visit only those nodes that are located within the first couple of node levels.

Note that the default level-order tree traversal will visit the nodes in tree
order (ancestors before descendants) and also according to the tree's child
order (if one exists). Because of that, the (default) level-order traversal
is **order preserving**.
