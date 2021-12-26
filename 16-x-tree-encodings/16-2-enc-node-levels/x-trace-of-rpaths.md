
<!-- ======================================================================= -->
# a pre-order trace of rooted paths

A trace of rooted paths in pre-order can be formed as follows.

```js
traceOfRps(root) begin
  trace = ()

  pathOf(rpath, node) begin
    if (node !== root) begin
      pathOf(rpath, node.parent)
    end
    rpath.append(node)
  end

  visitInPreOrder(node) begin
    //- visit the current node
    rpath = ()
    pathOf(rpath, node)
    trace.append(rpath)

    //- visit the child nodes
    for(child in node.childNodesFTL) begin
      visitInPreOrder(child)
    end
  end

  visitInPreOrder(root)
  return trace
end
```

<!-- ======================================================================= -->

Note that ...

* since the rooted paths are in pre-order,
* the first path is that of the tree's root,
* the root node is the first node in each path,
* no path in the pre-order trace of rooted paths is empty.

Each path contains all those nodes whose scopes have been entered, but not
yet exited, while the last node of a path is being visited. Hence, a rooted
path corresponds with a stack of defining nodes.

If each path in the trace of rooted paths is replaced by its last node,
the sequence will be transformed into the tree's pre-order trace of nodes.

If each path in the trace of rooted paths is replaced by its node-length,
the sequence will be transformed into a sequence of level values in pre-order.
