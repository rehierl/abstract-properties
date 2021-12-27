
<!-- ======================================================================= -->
# the level-based encoding, in level order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
                                                    f   g
```

Note that the level values are monotone increasing with each subsequent node.

* `(n[i].lvl <= n[j].lvl)` is true for `(1 <= i) && (i < j) && (j <= #n)`

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
    n.append(node)

    //- visit the current node
    level = node.parentNode.lvl
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

Note that, as before, the document tree's root obviously has no parent of its
own, which is why `node.parentNode.lvl` will in general trigger an error.
As a matter of clarity, this line is kept as is.

<!-- ======================================================================= -->
## decoding

Note that the sequence of level values produced by a level-order traversal
**can not be used to decode a document tree**. That is because one can not
reliably tell to which parent a node in the sequence belongs.

* nodes `e` and `i` have distinct parents, while being on the same level
* node `e` - parent index `3` and node level `3`
* node `i` - parent index `4` and node level `3`

Note that, in order to be able to decode a tree from its sequence of level
values, the level values of the child nodes of a parent must be separated
from the level values of the child nodes of a subsequent parent, which the
pre-order traversal will do.
