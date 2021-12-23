
<!-- ======================================================================= -->
# the parent-based encoding, in reversed post-order

```
       a           reversed post-order
---------------    ----------------------------------------
 b    c      h     i  h  g  f  e  d  c  b  a - n, nodes
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.id
    d   e    i     2  9  5  5  7  7  9  9  x - d, parent.id
      -----
      f   g
```

Note that these sequences can be formed by the following algorithm.

```js
//- the default post-order traversal
traverseInPreOrder(root) begin
  n=(), r=(), d=()

  visitInPreOrderLTF(node) begin
    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPreOrderLTF(child)
    end

    //- visit the current node
    n.append(node)
    node.id = n.length
    r.append(node.id)
  end

  visitInPreOrderLTF(root)

  for (node in n) begin
    d.append(node.parentNode.id)
  end

  return n,r,d
end
```

<!-- ======================================================================= -->
## remarks
