
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

Note that the sequence of level values in post-order can not be used to easily
decode the document tree. That is because once a given node is reached, one
simply does not have the necessary information that would allow to directly
determine the current node's parent. After all, the amount of child nodes of
any node is unrestricted, which is why on can not determine the parent of a
node amongst those nodes that are subsequent to the current node.

Note however that it would in general be possible to lookup the current node's
parent, assumed that a presequent pass has pre-created all the nodes, which
would then allow to maintain a to-be-resolved list of nodes per node level.
However, this would require an additional complexity that is beyond the scope
of this discussion.
