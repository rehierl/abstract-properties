
<!-- ======================================================================= -->
# the parent-based encoding, in default pre-order

```
       a           default pre-order
---------------    ----------------------------------------x
 b    c      h     a  b  c  d  e  f  g  h  i - n, trace
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.idx
    d   e    i     x  1  1  3  3  5  5  1  8 - d, parent.idx
      -----
      f   g
```

Note that this document tree is such that its nodes are labeled with
alphabetical letters in ascending order according to the pre-order tree
traversal. Because of that, sequence `n` contains the first 9/nine letters
in ascending order.

<!-- ======================================================================= -->
## encoding

The above sequences can be formed by the following algorithm.

```js
encode(root) begin
  n=(), r=(), d=()

  visitInPreOrderFTL(node) begin
    //- visit the current node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
    d.append(node.parentNode.idx)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end
  end

  visitInPreOrderFTL(root)
  return n,d
end
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, d) begin
  assert((0 < #n) and (#n == #d))
  assert(d[1] <= 0)
  nodes=(), roots=()

  for (i=1 to #n) begin
    current = new Node(n[i])
    nodes.add(current)
    parentRef = d[i]

    //- a root node
    if (parentRef <= 0) begin
      roots.add(current)
      continue
    end

    //- an invalid reference
    if (parentRef > #n) begin
      assert(false)
    end

    //- a cyclic graph
    if (parentRef >= i) begin
      assert(false)
    end

    parent = nodes[parentRef]
    parent.addAsLastChild(current)
  end

  return roots
end
```

Note that this pseudocode is identical to that of the level-order traversal.
