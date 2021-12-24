
<!-- ======================================================================= -->
# the parent-based encoding, in reversed post-order

```
       a           reversed post-order
---------------    ----------------------------------------
 b    c      h     i  h  g  f  e  d  c  b  a - n, trace
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.idx
    d   e    i     2  9  5  5  7  7  9  9  x - d, parent.idx
      -----
      f   g
```

<!-- ======================================================================= -->
## encoding

The above sequences can be formed by the following algorithm.

```js
encode(root) begin
  n=(), r=(), d=()

  visitInPostOrderLTF(node) begin
    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPostOrderLTF(child)
    end

    //- visit the current node
    n.append(node)
    node.idx = n.length
  end

  visitInPostOrderLTF(root)

  for (node in n) begin
    r.append(node.idx)
    d.append(node.parentNode.idx)
  end

  return n,d
end
```

<!-- ======================================================================= -->
## decoding

Note that, as above, this decoding algorithm would only differ from the
algorithm of the default traversal in the expression that adds the current
node as a child to its parent. Hence, no pseudocode will be listed.

* `.addAsFirstChild()` instead of `.addAsLastChild()`
