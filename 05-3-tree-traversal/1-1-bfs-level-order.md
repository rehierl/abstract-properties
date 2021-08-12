
<!-- ======================================================================= -->
# breadth-first search (BFS), level order

A tree traversal is referred to as a breadth-first search (BFS), if the nodes
within a tree are visited one node level at a time, and beginning with the
specified root node.

```
//- the default level-order traversal
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

Note that several variations are possible. One possibility is to visit the child
nodes in reverse. Also, the tree traversal can in principle be restricted to
visit only those nodes that are located within the first couple of node levels.

Note that the default BFS tree traversal will visit the nodes in tree order
(ancestors before descendants) and also according to the tree's child order
(if one exists). Because of that, the (default) BFS tree traversal is
**order preserving**.
