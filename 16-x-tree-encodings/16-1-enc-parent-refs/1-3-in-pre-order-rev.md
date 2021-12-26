
<!-- ======================================================================= -->
# the parent-based encoding, in reversed pre-order

```
reversed pre-order (PRER)                           a
-----------------------------------------    ---------------
a  h  i  c  e  g  f  d  b - n, trace          b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx          -----   ---
x  1  2  1  4  5  5  4  1 - par, parent.idx      d   e    i
                                                   -----
                                                   f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  n=(), r=(), par=()

  visitInPreOrderLTF(node) begin
    //- visit the current node
    n.append(node)

    node.idx = n.length
    r.append(node.idx)

    parRef = node.parentNode.idx
    par.append(parRef)

    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPreOrderLTF(child)
    end
  end

  visitInPreOrderLTF(root)
  return n,par
end
```

<!-- ======================================================================= -->
## decoding

Note that, as above, this decoding algorithm would only differ from the
algorithm of the default traversal in the expression that adds the current
node as a child to its parent. Hence, no pseudocode will be listed.

* `.addAsFirstChild()` instead of `.addAsLastChild()`
