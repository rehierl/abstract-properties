
<!-- ======================================================================= -->
# the level-based encoding, in post-order

```
default post-order (POST)                           a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
                                                    f   g
```

Note that no pseudocode for the reversed versions will be provided.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lvl` can be formed as follows.

```js
encode(root) begin
  n=(), lvl=()
  level = 0

  visitInPreOrderFTL(node) begin
    //- enter the node's type-1 scope
    level = (level + 1)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end

    //- visit the current node
    n.append(node)
    lvl.append(level)

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,lvl
end
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, lvl) begin
  assert((0 < #n) and (#n == #lvl))
  assert(lvl[#n] == 1)//- must be a root
  nodes=(), roots=(), rp=()

  for (i=#n to #1) begin
    current = new Node(n[i])
    nodes.append(current)

    level = lvl[i]
    assert(level >= 1)
    current.lvl = level

    //- if the current node is a root
    if (level == 1) begin
      roots.append(current)
      rp.setLast(level, current)
      continue
    end

    //- assert that the input level does
    //  not exceed the range [1,#rp+1]
    //- level values are no rank values!
    parent = rp.currentLast
    assert(level <= (parent.lvl+1))

    //- the node is a child to a node in rp
    parent = rp[level-1]
    parent.addAsFirstChild(current)
    rp.setLast(level, current)
  end

  return roots
end
```

Note that, since the ancestors of a node appear subsequent to it, the sequence
of level values must be read in reverse from last to first. That is because
ancestors will then be encountered before any of their descendants. After all,
the tree order is still a suborder to the reversed POST and POSTR traces.

* hence the `.addAsFirstChild()` method call
