
<!-- ======================================================================= -->
# the length-based encoding, in default level-order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
9  1  5  2  1  3  1  1  1 - len, node.len           f   g
```

Note that the length values in default level-order are not monotone decreasing.

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

    //- store the node count with each node
    node.len = count
    return count
  end

  //- traverse in level order
  visitInLevelOrder(node) begin
    next = new Queue()
    next.enqueue(root)

    while (next.isEmpty() == false) begin
      node = next.dequeue()

      //- visit the node
      n.append(node)
      len.append(node.len)

      //- plan the visit of each child
      for (child in node.childNodesFTL) begin
        next.enqueue(child)
      end
    end
  end

  //- pre-determine all node counts
  count = countNodes(root)

  visitInLevelOrder(root)
  return n,len
end
```

Note that the computational complexity is improved at the cost of increased
storage requirements - i.e. `node.len`. Without that storage property, the
algorithm would have exponential runtime complexity since one would have to
determine the node count of a node with each visit.

<!-- ======================================================================= -->
## decoding

Note that the sequence of length values produced by a level-order traversal
**can not be used to easily decode a document tree**. That is because one
can not reliably tell to which parent a node in the level-order trace belongs.

Note that the node count of a node must be such that its value minus one is
the sum of lengths of one or more complete child orders. With that in mind
one could imagine a sequence of child orders for which it is not possible to
uniquely resolve these sums - i.e. there might be more than one possibility.
