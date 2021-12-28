
<!-- ======================================================================= -->
# the parent-based encoding, in default post-order

```
default post-order (POST)                            a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  n=(), r=(), par=()

  visitInPostOrderFTL(node) begin
    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPostOrderFTL(child)
    end

    //- visit the node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
  end

  visitInPostOrderFTL(root)

  for (idx=1 to #n) begin
    parent = n[idx].parentNode
    parRef = parent ? parent.idx : #n+1
    par.append(parRef)
  end

  return n,par
end
```

Note that, since this traversal will visit a node after all of its descendants
in the unordered document tree (DTU) have been visited, parent nodes have no
index associated once a child is being visited. To circumvent this issue, a
second pass over all the nodes may be used in order to populate the sequence
of parent references.

Note that alternative methods are possible, which can be used to circumvent a
second pass. However, all alternatives have in common that they will increase
the computational complexity compared to LVL, PRE and PRER.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[#par] > #n)//- must be a root
  nodes=(), roots=()

  for (i=#n to 1) begin
    node = new Node(n[i])
    nodes.append(node)
    parRef = par[i]

    //- a root node
    if (parRef > #n) begin
      roots.append(node)
      continue
    end

    //- an invalid reference
    if (parRef <= 0) begin
      assert(false)
    end

    //- a cyclic graph
    if (parRef <= i) begin
      assert(false)
    end

    //- parRef in [i,#n]
    parent = nodes[parRef]
    parent.addAsFirstChild(node)
  end

  return roots
end
```

Recall that the POST and POSTR traversals are forward-oriented. That is,
each node `c` has a parent `p` that is subsequent to it in the trace of
nodes `n`.

* `(p subsequent-to c)` is true for `(p ancestor-of c)`

Note that, even though the tree order is no suborder to the corresponding
trace, it still is a suborder to the reversed trace.

Note that, in the context of a forward-oriented encoding, the invalid
reference (x) is assumed to have a positive value of `#n+1`.
