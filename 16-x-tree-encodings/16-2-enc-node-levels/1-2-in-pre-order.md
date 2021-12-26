
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

Note that pseudocode for the reversed version will not be specified.

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

    //- visit the current node
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
of that, the level of a node increases by one each time a scope is entered
and decreases by one each time a scope is exited. Because of that, there is
no issue in regards to having to determine the parent's node level of a node.

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
    current = new Node(n[i])
    nodes.add(current)

    level = lvl[i]
    assert(level >= 1)
    current.lvl = level

    //- if the current node is a root
    if (level == 1) begin
      roots.add(current)
      rp.setLast(level, current)
      continue
    end

    //- assert that the input level does
    //  not exceed valid limits
    //- level values are no rank values!
    parent = rp.currentLast
    assert(level <= (parent.lvl+1))

    //- the current node is now guaranteed to
    //  be a child of one of the nodes in 'rp'
    parent = rp[level-1]
    parent.addAsLastChild(current)
    rp.setLast(level, current)
  end

  return roots
end
```

Recall that the PRE and the PRER traversal is backward-oriented. That is, each
node `c` has a parent `p` that is presequent to it in the sequence of node
definitions `n`. After all, the tree order is as a suborder embedded into the
corresponding traces.

* `(p presequent-to c)` for `(p ancestor-of c)` is true

Note that sequence `rp` is intended to maintain a rooted path as a sequence of
nodes. Usually, this would be implemented as a stack of nodes. However, since
a stack maintains its elements in reverse, this option was not chosen as a
matter of clarity.

Note that expression `rp.setLast(level, current)` is expected to first ensure
that the array's capacity is such that the given node can be set at the
specified level. Furthermore, the expression is expected to set the current
node at the specified level. Finally, the specified level is used to update
the rooted path such that the node being set is treated as the new last node,
which can be retrieved via the expression `rp.currentLast`.

Note that the above decoding algorithm is **similar to rank-based algorithms**.
That is because the current node, assuming all is in order, always is a child
to one of the nodes in the current rooted path. (More detailed explanations
will follow eventually ..).
