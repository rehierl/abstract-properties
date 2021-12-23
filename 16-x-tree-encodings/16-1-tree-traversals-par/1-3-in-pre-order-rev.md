
<!-- ======================================================================= -->
# the parent-based encoding, in reversed pre-order

```
       a           reversed pre-order
---------------    ----------------------------------------
 b    c      h     a  h  i  c  e  g  f  d  b - n, nodes
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.id
    d   e    i     x  1  2  1  4  5  5  4  1 - d, parent.id
      -----
      f   g
```

Note that these sequences can be formed by the following algorithm.

```js
//- the reversed pre-order traversal
traverseInPreOrder(root) begin
  n=(), r=(), d=()

  visitInPreOrderLTF(node) begin
    //- visit the current node
    n.append(node)
    node.id = n.length
    r.append(node.id)
    d.append(node.parentNode.id)

    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPreOrderLTF(child)
    end
  end

  visitInPreOrderLTF(root)
  return n,r,d
end
```

<!-- ======================================================================= -->
## remarks
