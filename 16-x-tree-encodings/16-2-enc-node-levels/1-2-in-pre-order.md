
<!-- ======================================================================= -->
# the level-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
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

Note that the level of a node is equal to the number of nodes in its rooted
path, which is why a level value reflects the number of open scopes a the
time a node is being visited. Because of that, the level of a node increases
by one each time a scope is entered, and decreases by one each time a scope
is exited. Consequently, there is no issue when having to determine the level
of a root. That is because one does not require access to a parent object in
order to determine the level of a node.

* `level+1` each time a scope is entered
* `level-1` each time a scope is exited

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming 'n' is in pre-order
decode(n, lvl) begin
  assert((0 < #n) and (#n == #lvl))
  assert(lvl[1] == 1)//- must be a root
  nodes=(), roots=(), rp=()
  last = 0

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)

    level = lvl[i]
    assert(level >= 1)
    node.lvl = level

    //- assert that the input level does
    //  not exceed the valid range [1,#rp+1]
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
    parent.addAsLastChild(node)
  end

  return roots
end
```

Note that the rooted path `rp` is used as a hashtable. That is, considerations
in regards to some capacity can be ignored at this point.
