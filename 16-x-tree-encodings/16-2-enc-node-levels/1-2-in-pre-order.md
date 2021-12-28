
<!-- ======================================================================= -->
# the level-based encoding, in pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
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

    //- visit the node
    n.append(node)
    lvl.append(level)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,lvl
end
```

Note that the level of a node is equal to the number of open scopes. Because
of that, the level of a node increases by one each time a scope is entered,
and decreases by one each time a scope is exited. Because of that, there is
no issue when having to determine the level of a root node.

* `level+1` each time a scope is entered
* `level-1` each time a scope is exited

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, lvl) begin
  assert((0 < #n) and (#n == #lvl))
  assert(lvl[1] == 1)//- must be a root
  nodes=(), roots=(), rp=()

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)

    level = lvl[i]
    assert(level >= 1)
    node.lvl = level

    //- if the node is a root
    if (level == 1) begin
      roots.append(node)
      rp.setLast(level, node)
      continue
    end

    //- assert that the input level does
    //  not exceed the range [1,#rp+1]
    //- level values are no rank values!
    last = rp.currentLast
    assert(level <= (last.lvl+1))

    //- the node is a child to a node in rp
    parent = rp[level-1]
    parent.addAsLastChild(node)
    rp.setLast(level, node)
  end

  return roots
end
```

Note that sequence `rp` is intended to maintain a rooted path as a sequence
of nodes. Usually, this would be implemented as a stack of nodes. However,
since a stack maintains its elements in reverse, one needs to think of `rp`
as a simple hashtable.

Note that expression `rp.setLast(level, node)` is expected to set the given
node at the specified level. Furthermore, the call is expected to maintain a
reference of the node that was set last, and which can be retrieved via the
rooted path's `.currentLast` property.

Note that the above decoding algorithm is **similar to rank-based algorithms**.
That is because the current node, assuming all is in order, always is a child
to one of the nodes in the current rooted path. (More detailed explanations
will follow eventually).
