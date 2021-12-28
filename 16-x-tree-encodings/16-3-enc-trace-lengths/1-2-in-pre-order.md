
<!-- ======================================================================= -->
# the length-based encoding, in pre-order order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
```

Note that no pseudocode for the reversed versions will be provided.

<!-- ======================================================================= -->
## encoding - TODO

Sequences `n` and `len` can be formed as follows.

```js
encode(root) begin
  n=(), len=(), nc=()
  level = 0

  visitInPreOrderFTL(node) begin
    //- enter the node's type-1 scope
    level = (level + 1)

    //- visit the node
    n.append(node)
    node.idx = n.length

    //- initialize the node count to an invalid
    //  value, which will be replaced on exit
    len.append(0)

    //- initialize the node counter for the
    //  current node - by counting itself
    nc[level] = 1

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)

      //- add the number of nodes of the
      //  induced subtree T[child] to the
      //  node count of the current node
      nc[level] = nc[level] + nc[level+1]
    end

    //- write the node count
    count = nc[level]
    len[node.idx] = count

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,len
end
```

Note that a hashtable of counter values (i.e. `nc`, read as "node count" )
is used to determine the node count of each node, one node at a time.

Note that the post-order version is straight forward since the node count of
a node will be available when the node and its node count need to be written
to the corresponding sequences. In contrary to that, this pre-order version
requires to memorize the index of a node such that its initialized node count
can be replaced by its final node count.

Note that the above pseudocode incorporates aspects of a pre-order, of an
in-order and also aspects of a post-order traversal. That is because certain
operations must be executed before visit of its first child, during the visit
of its child nodes, and also after the visit of its last child.

<!-- ======================================================================= -->
## decoding - TODO

The encoded tree can be recreated as follows.

```js
decode(n, len) begin
  assert((0 < #n) and (#n == #len))
  assert(len[1] == #n)//- must be a root
  assert(len[#n] == 1)//- must be a leaf
  nodes=(), roots=()
  rp = new RootedPath()

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)

    count = len[i]
    rp.push(node, count)

    if (#rp == 1) begin
      roots.append(node)
    end

    if (#rp > 1) begin
      parent = rp.parent()
      parent.addAsLastChild(node)
    end

    rp.pop()
  end

  assert(#rp == 0)
  return roots
end
```

Note that the rooted path `rp` is no simple stack, but a stack with extended
functionality. This additional functionality has the purpose of counting down
the length values, which is used to keep track of the nodes in the rooted
path.

Recall that the scope of a node and its pre-order trace of nodes have the same
sets of nodes. Because of that, the node's scope appears as a substring to the
document tree's pre-order trace. Hence, the length value of a node counts the
number of nodes, beginning with the current node, that are part of the node's
scope.

* `s(n) := len[i,i+N-1]` for `(len[i] == N)` and `(i in [1,#len])`

Note that the first length entry must therefore be equal to the length of the
sequence of length values - i.e. `(len[1] == #len)`. That is because the scope
of a root includes all the nodes. Likewise, the last length entry must have a
value of one - i.e. `(len[#len] == 1)`. That is because the scope of a leaf
only contains the corresponding leaf.

Note that the above pseudocode is only artificially reduced to a single tree.
That is, the entry assertions are in general not required.
