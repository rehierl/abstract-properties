
<!-- ======================================================================= -->
# the parent-based encoding, in default pre-order

```
default pre-order (PRE)                               a
-------------------------------------------    ---------------
a  b  c  d  e  f  g  h  i - n, trace            b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx            -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx        d   e    i
                                                     -----
                                                     f   g
```

Note that the document tree is such that its nodes are labeled with alphabetical
letters in ascending order according to the pre-order tree traversal. Because
of that, sequence `n` contains the first 9/nine letters in ascending order.

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  n=(), r=(), par=()

  visitInPreOrderFTL(node) begin
    //- visit the current node
    n.append(node)

    node.idx = n.length
    r.append(node.idx)

    parRef = node.parentNode.idx
    par.append(parRef)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end
  end

  visitInPreOrderFTL(root)
  return n,par
end
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[1] <= 0)
  nodes=(), roots=()

  for (i=1 to #n) begin
    current = new Node(n[i])
    nodes.add(current)
    parRef = par[i]

    //- a root node
    if (parRef <= 0) begin
      roots.add(current)
      continue
    end

    //- an invalid reference
    if (parRef > #n) begin
      assert(false)
    end

    //- a cyclic graph
    if (parRef >= i) begin
      assert(false)
    end

    parent = nodes[parRef]
    parent.addAsLastChild(current)
  end

  return roots
end
```

Note that this pseudocode is identical to that of the level-order traversal.
