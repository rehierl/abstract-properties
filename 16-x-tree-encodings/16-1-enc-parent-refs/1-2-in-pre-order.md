
<!-- ======================================================================= -->
# the parent-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

Note that the document tree is such that its nodes are labeled with alphabetical
letters in ascending order with regards to the pre-order tree traversal. Because
of that, sequence `n` contains the first 9/nine letters in ascending order.

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  n=(), r=(), par=()

  visitInPreOrderFTL(node) begin
    //- visit the node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
    parent = node.parentNode
    parRef = parent ? parent.idx : 0
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
//- assuming 'n' is in level-order
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[1] <= 0)//- must be a root
  nodes=(), roots=()

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)
    parRef = par[i]

    //- a root node
    if (parRef <= 0) begin
      roots.append(node)
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

    //- parRef in [1,i]
    parent = nodes[parRef]
    parent.addAsLastChild(node)
  end

  return roots
end
```

Recall that the PRE traversal is backward-oriented. That is, each node `c` has
a parent `p` that is presequent to it in trace `n`. After all, the tree order
is a suborder to the corresponding trace.

* `(p presequent-to c)` is true for `(p ancestor-of c)`
