
<!-- ======================================================================= -->
# the parent-based encoding, in reversed post-order

```
reversed post-order (POSTR)                          a
-------------------------------------------   ---------------
i  h  g  f  e  d  c  b  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
2  9  5  5  7  7  9  9  x - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  n=(), r=(), par=()

  visitInPostOrderLTF(node) begin
    //- visit the child nodes
    for (child in node.childNodesLTF) begin
      visitInPostOrderLTF(child)
    end

    //- visit the node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
  end

  visitInPostOrderLTF(root)

  for(idx=1 to #n) begin
    parent = n[idx].parentNode
    parRef = parent ? parent.idx : #n+1
    par.append(parRef)
  end

  return n,par
end
```

<!-- ======================================================================= -->
## decoding

Note that, as above, this decoding algorithm would only differ from the
algorithm of the default traversal in the expression that adds the current
node as a child to its parent. Hence, no pseudocode will be listed.

* `.addAsFirstChild()` instead of `.addAsLastChild()`
