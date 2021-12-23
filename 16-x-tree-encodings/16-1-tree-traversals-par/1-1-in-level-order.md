
<!-- ======================================================================= -->
# the parent-based encoding, in level order

```
       a           level-order
---------------    ----------------------------------------
 b    c      h     a  b  c  h  d  e  i  f  g - n, nodes
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.id
    d   e    i     x  1  1  1  3  3  4  6  6 - d, parent.id
      -----
      f   g
```

Note that these sequences can be formed by the following algorithm.

```js
//- the default level-order traversal
traverseInLevelOrder(root) begin
  next = new Queue()
  next.enqueue(root)
  n=(), r=(), d=()

  while (next.isEmpty() == false) begin
    node = next.dequeue()

    //- visit the current node
    n.append(node)
    node.id = n.length
    r.append(node.id)
    d.append(node.parentNode.id)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      next.enqueue(child)
    end
  end

  //- sequences n,r,d are now complete
  return n,r,d
end
```

<!-- ======================================================================= -->
## remarks

Note that the document tree's root obviously has no parent of its own. Hence,
the line that is to append the id of the current node's parent to sequence `d`
would trigger an error. Despite that, and as a matter of clarity, this line is
kept as is.
