
<!-- ======================================================================= -->
# the parent-based encoding, in reversed pre-order

```
       a           reversed pre-order
---------------    -----------------------------------------
 b    c      h     a  h  i  c  e  g  f  d  b - n, trace
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.idx
    d   e    i     x  1  2  1  4  5  5  4  1 - d, parent.idx
      -----
      f   g
```

<!-- ======================================================================= -->
## encoding

The above sequences can be formed by the following algorithm.

```js
encode(root) begin
  n=(), r=(), d=()

  visitInPreOrderLTF(node) begin
    //- visit the current node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
    d.append(node.parentNode.idx)

    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPreOrderLTF(child)
    end
  end

  visitInPreOrderLTF(root)
  return n,d
end
```

<!-- ======================================================================= -->
## decoding

Note that, as above, this decoding algorithm would only differ from the
algorithm of the default traversal in the expression that adds the current
node as a child to its parent. Hence, no pseudocode will be listed.

* `.addAsFirstChild()` instead of `.addAsLastChild()`
