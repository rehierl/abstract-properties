
- a sequence of depth values reflects a height-map
- seems like it would be helpful to explain
- issue with siblings that have no child nodes?
- could be translated to a length-based encoding?

<!-- ======================================================================= -->
# trace of rooted paths

Any tree traversal can be used to produce an ordered sequence of rooted paths,
which could be referred to as **a trace of (rooted) paths**. Even though it might
seem silly to produce such a trace, especially since one can produce an ordinary
trace of nodes, the following considerations might still make it worth while:

* each node in a tree has one unique rooted path
* each node will be visited once only - strict traversal
* each rooted path reflects all of the node's ancestors
* each rooted path reflects the node's node level/depth
* rooted paths are either related ex-or they overlap each other

```
traceOfRps(root) begin
  sequence = ()

  pathOf(rpath, node) begin
    if(node.parent != null) begin
      pathOf(rpath, node.parent)
    end
    rpath.append(node)
  end

  visit(node) begin
    rpath = ()
    pathOf(rpath, node)
    sequence.append(rpath)
  end

  traverseInPreOrder(node) begin
    visit(node)

    for(child in node.childNodes) begin
      traverseInPreOrder(child)
    end
  end

  traverseInPreOrder(root)
  return sequence
end
```

<!-- ======================================================================= -->

Note the following ...

* since the rooted paths are in pre-order
* the first path is that of the tree's root - length 1
* the root node is the first node in each path
* no path in this trace is empty

Each path contains all those nodes that have been entered, but not yet exited
while the node is being visited. Hence **a (current) stack of open nodes**.

If each path in the sequence is replaced with the last node it holds, the trace
will then be the corresponding trace of nodes.

<!-- ======================================================================= -->

Note that this is in regards to the length-based encoding of the structure of
the corresponding node tree. Hence, the sequence of rooted paths could (e.g.)
lead to a depth-based encoding.

* replace each path in that trace by its length - the node's depth
* a simple +1/-1 per enter/exit
* a sequence of depth values

Can the tree's structure be recreated based on such a sequence of depth values?
Me thinks yes.

How efficient would it be?
What about post-order?
