
<!-- ======================================================================= -->
# the level-based encoding, in default level-order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
                                                    f   g
```

Note that the level values in a level-order trace are monotone increasing.

* `(lvl[i] <= lvl[j])` is true for `(1 <= i) && (i < j) && (j <= #n)`

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lvl` can be formed as follows.

```js
encode(root) begin
  next = new Queue()
  next.enqueue(root)
  n=(), lvl=()

  while (next.isEmpty() == false) begin
    node = next.dequeue()

    //- visit the node
    n.append(node)
    parent = node.parentNode
    level = parent ? parent.lvl : 0
    node.lvl = (level + 1)
    lvl.append(node.lvl)

    //- plan the visit of each child
    for (child in node.childNodesFTL) begin
      next.enqueue(child)
    end
  end

  return n,lvl
end
```

<!-- ======================================================================= -->
## decoding

Note that the sequence of level values produced by a level-order traversal
**can not be used to decode a document tree**. That is because one can not
reliably tell to which parent a node in the sequence belongs.

* node `e` - parent index `3` and node level `3`
* node `i` - parent index `4` and node level `3`
* i.e. despite being on the same level, `e` and `i` have distinct parents

Note that, in order to allow to decode a tree from its sequence of level values,
the level values of child nodes must be separated from the level values of child
nodes that belong to a subsequent parent, which the pre-order traversal will do.
