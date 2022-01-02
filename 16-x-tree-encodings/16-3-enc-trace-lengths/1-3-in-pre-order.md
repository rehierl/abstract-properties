
<!-- ======================================================================= -->
# the length-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `len` can be formed as follows.

```js
encode(root) begin
  n=(), len=(), rp=(), nc=()
  level = 0

  visitInPreOrderFTL(node) begin
    //- enter the node's type-1 scope
    level = (level + 1)

    //- visit the node
    n.append(node)
    offset = n.length
    rp[level] = offset

    //- initialize the node count to an invalid
    //  value, which will be replaced on exit
    //- stored in len[node.idx]
    len.append(0)

    //- initialize the counter for the current
    //  node - by including/counting itself
    nc[level] = 1

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)

      //- add the number of nodes of the
      //  induced subtree T[child] to the
      //  node count of the current node
      nc[level] = nc[level] + nc[level+1]
    end

    //- overwrite the initialized node count
    offset = rp[level]
    length = nc[level]
    len[index] = length

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,len
end
```

Note that **a hashtable** of offset values `rp` (read as "rooted path") is
used to maintain the offset indexes of the nodes in the current rooted path.
Likewise, a hashtable of counter values `nc` (read as "node count") is used
to sum up the node count of each node.

Note that the post-order version is straight forward since the node count of
a node will be available when the node and its node count need to be appended
to the corresponding sequences. In contrary to that, the pre-order version
requires to memorize the index of a node such that its initialized node count
can be replaced by the final value.

Note that the above pseudocode incorporates aspects of a pre-order, aspects of
an in-order and also aspects of a post-order traversal. That is because some
operations must be executed before the visit of its first child, some during
the visit of its child nodes, and some after the visit of its last child.

<!-- ======================================================================= -->
## encoding (2)

Note that one is in general not required to explicitly count the nodes. That
is because the final length of a trace can be derived from the index of its
first node and the index of its last node.

- see the end-based encoding scheme

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming 'n' is in pre-order
decode(n, len) begin
  assert((0 < #n) and (#n == #len))
  //- assuming a single document tree
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

    //- reduce the node count of each node
    //  and pop all the nodes that have a
    //  remaining node count of 0/zero
    rp.pop()
  end

  assert(#rp == 0)
  return roots
end
```

Note that the rooted path `rp` is no simple stack, but a stack with extended
functionality. This additional functionality has the purpose of counting down
the length values, which is used to keep track of the nodes in the current
rooted path, which allows to determine the parent of the next subsequent node.

Recall that the scope of a node and its pre-order trace have the same sets of
nodes. Because of that, the scope of a node can be described to appear as a
substring to the document tree's pre-order trace `n`. Hence, the length value
of a node `x` is equal to the length of the node's pre-order trace `pre(x)`.

* `pre(x) := n[i,i+N-1]` is true assuming ..
* `(n[i] == x)` and `(len[i] == N)` for `(i in [1,#len])`

Note that the first length entry must be equal to the length of the sequence
of length values - i.e. `(len[1] == #len)`. That is because the scope of a
root includes all the nodes. Likewise, the last entry must have a value of
one - i.e. `(len[#len] == 1)`. That is because the scope of a leaf only
contains the leaf itself.

Note that, due to the entry assertions, the above pseudocode is artificially
reduced to a single tree. That is, the 2nd and 3rd entry assertions must be
altered or dropped if the sequence of length values defines the structure of
a forest of trees. That is because no length value can then be equal to the
length of the sequence of length values.
