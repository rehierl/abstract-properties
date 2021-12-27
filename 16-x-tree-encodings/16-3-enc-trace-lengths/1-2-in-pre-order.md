
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

    //- visit the current node
    //- initialize the node count to an invalid
    //  value, which will be replaced on exit
    n.append(node)
    node.idx = n.length
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

    //- replace the initial node count
    count = nc[level]
    len[node.idx] = count

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,len
end
```

Note that a stack of counter values (i.e. `nc`, read as "node count" ) is used
to determine the node count of each node, one node at a time.

Note that the post-order version is straight forward since the node count of
a will be available when the node and its node count need to be written to the
corresponding sequences. In contrary to that, this pre-order version requires
to memorize the index of a node such that its initialized node count can be
replaced by the actual node count.

<!-- ======================================================================= -->
## decoding - TODO
