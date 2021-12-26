
<!-- ======================================================================= -->
# the parent-based encoding, in default post-order

```
default post-order (POST)                           a
-----------------------------------------    ---------------
b  d  f  g  e  c  i  h  a - n, trace          b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx          -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx      d   e    i
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

    //- visit the current node
    n.append(node)
    node.idx = n.length
  end

  visitInPostOrderFTL(root)

  for (node in n) begin
    r.append(node.idx)

    parRef = node.parentNode.idx
    par.append(parRef)
  end

  return n,par
end
```

Note that, since this traversal will visit a node only after all of its
descendants in the unordered document tree (DTU) have been visited, parent
nodes have in general no id associated once a child is being visited. To
circumvent this issue, a second pass over all the nodes may be used in
order to fill the sequence of parent references.

Note that alternative methods are possible which can be used to circumvent a
second pass. However, all alternatives have in common that they will increase
the computational complexity compared to LVL, PRE and PRER.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[#par] <= 0)
  nodes=(), roots=()

  //- first, create all node objects
  for (i=1 to #n) begin
    current = new Node(n[i])
    nodes.add(current)
  end

  //- interconnect the node objects
  for (i=1 to #n) begin
    current = nodes[i]
    parRef = par[i]

    //- a root node
    if (parRef > #n) begin
      roots.add(current)
      continue
    end

    //- an invalid reference
    if (parRef <= 0) begin
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

Note that, as before, since the parent references are forwards-oriented,
a first pass is used to pre-create all the node objects such that they are
accessible by the second pass.
