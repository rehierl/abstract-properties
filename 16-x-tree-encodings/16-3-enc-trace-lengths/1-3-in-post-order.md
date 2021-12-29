
<!-- ======================================================================= -->
# the length-based encoding, in default post-order

```
default post-order (POST)                            a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
1  1  1  1  3  5  1  2  9 - len, node.len           f   g
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

    //- visit the node
    n.append(node)

    //- write the node count
    count = nc[level]
    len.append(count)

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,len
end
```

Note that a hashtable of counter values `nc` (read as "node count") is
used to determine the node count of each node, one node at a time.

Note that, compared to the pre-order version, this post-order version is
straight forward since a node and its node count will be appended to the
corresponding sequences once the node's scope is being exited.

<!-- ======================================================================= -->
## decoding - TODO

The encoded tree can be recreated as follows.

```js
//- assuming 'n' is in post-order
decode(n, len) begin
  assert((0 < #n) and (#n == #len))
  //- assuming a single document tree
  assert(len[#n] == #n)//- must be a root
  assert(len[1] == 1)//- must be a leaf
  nodes=(), roots=()
  rp = new RootedPath()

  for (i=#n to 1) begin
    node = new Node(n[i])
    nodes.append(node)

    count = len[i]
    rp.push(node, count)

    if (#rp == 1) begin
      roots.append(node)
    end

    if (#rp > 1) begin
      parent = rp.parent()
      parent.addAsFirstChild(node)
    end

    rp.pop()
  end

  assert(#rp == 0)
  return roots
end
```
