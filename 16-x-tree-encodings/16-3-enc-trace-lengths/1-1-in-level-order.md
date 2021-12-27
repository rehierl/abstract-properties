
<!-- ======================================================================= -->
# the length-based encoding, in level order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
9  1  5  2  1  3  1  1  1 - len, node.len           f   g
```

Note that the length values are obviously not monotone decreasing.

<!-- ======================================================================= -->
## encoding - TODO

Sequences `n` and `len` can be formed as follows.

```js
encode(root) begin
  n=(), len=()

  //- recursively determine #D*(n)
  countNodes(node) begin
    //- count the node itself
    count = 1

    //- visit the child nodes
    for (child in node.childNodes) begin
      count = count + countNodes(child)
    end

    //- store the result with each node
    node.len = count
    return count
  end

  //- traverse in level order
  visitInLevelOrder(node) begin
    next = new Queue()
    next.enqueue(root)

    while (next.isEmpty() == false) begin
      node = next.dequeue()

      //- visit the current node
      n.append(node)
      len.append(node.len)

      //- plan the visit of each child
      for (child in node.childNodesFTL) begin
        next.enqueue(child)
      end
    end
  end

  //- ensure that all length values are available
  //  as .len properties attached to each node
  count = countNodes(root)

  visitInLevelOrder(root)
  return n,len
end
```

Note that the computational complexity is improved at the cost of increased
storage requirements (see `node.len`).

<!-- ======================================================================= -->
## decoding

Note that the sequence of length values produced by a level-order traversal
**can not be used to decode a document tree**. That is because one can not
reliabley tell to which parent a node in the sequence belongs, which is
why one can not determine the relationship of one length value with that
of a subsequent node.
