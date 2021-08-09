
<!-- ======================================================================= -->
# trace of nodes

Any tree traversal can be used to produce an ordered squence of nodes that is
commonly described as **a trace of nodes**, if the node that is being visited,
is appended to the sequence at the time it is being visited. Because of that,
such a trace of nodes reflects the path the traversal algorithm took through
the tree when visiting each node.

```
preOrderTraceOf(root) begin
  trace = ()

  traversInPreOrder(node) begin
    trace.append(node)

    for (child in node.childNodes) begin
        traverseInPreOrder(child)
    end
  end

  traverseInPreOrder(root)
  return trace
end
```

Even though any tree traversal can be used to produce a trace of nodes, the
algorithm as defined above will produce a trace of nodes that can be described
as **the pre-order trace of nodes** of the corresponding node tree, and even
as the pre-order trace of the specified node.

Note that, like any other ordered sequence, a trace of nodes corresponds with a
total order over the nodes of the tree that was traversed. As such, the process
of creating a trace of nodes corresponds with **a linear extension** of the
tree's node order, which can also be described as **a topological sorting**.
