
<!-- ======================================================================= -->
# the level-based encoding, in default post-order

```
default post-order (POST)                           a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
                                                    f   g
```

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

    //- visit the node
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
//- assuming 'n' is in post-order
decode(n, lvl) begin
  assert((0 < #n) and (#n == #lvl))
  assert(lvl[#n] == 1)//- must be a root
  nodes=(), roots=(), rp=()
  last = 0

  for (i=#n to #1) begin
    node = new Node(n[i])
    nodes.append(node)

    level = lvl[i]
    assert(level >= 1)
    node.lvl = level

    //- assert that the input level does
    //  not exceed the range [1,#rp+1]
    assert(level <= (last+1))
    rp[level] = node
    last = level

    //- if the node is a root
    if (level == 1) begin
      roots.append(node)
      continue
    end

    //- the node is a child to a node in rp
    parent = rp[level-1]
    parent.addAsFirstChild(node)
  end

  return roots
end
```

Note that, since the ancestors of a node appear subsequent to it, the sequence
of level values must be read in reverse from last to first. That is because
ancestors will then be encountered before any of their descendants. After all,
the tree order is still a suborder to the reversed POST and POSTR traces.

* hence the `.addAsFirstChild()` method call
