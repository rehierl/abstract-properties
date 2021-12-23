
<!-- ======================================================================= -->
# the parent-based encoding, in default pre-order

```
       a           default pre-order
---------------    ----------------------------------------
 b    c      h     a  b  c  d  e  f  g  h  i - n, nodes
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.id
    d   e    i     x  1  1  3  3  5  5  1  8 - d, parent.id
      -----
      f   g
```

Note that these sequences can be formed by the following algorithm.

```js
//- the default pre-order traversal
traverseInPreOrder(root) begin
  n=(), r=(), d=()

  visitInPreOrderFTL(node) begin
    //- visit the current node
    n.append(node)
    node.id = n.length
    r.append(node.id)
    d.append(node.parentNode.id)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end
  end

  visitInPreOrderFTL(root)
  return n,r,d
end
```

<!-- ======================================================================= -->
## remarks

Note that the above document tree is such that its nodes are labeled using
alphabetical letters and in ascending order according to the pre-order tree
traversal. Because of that, sequence `n` contains the first 10/ten letters
of in ascending order.
