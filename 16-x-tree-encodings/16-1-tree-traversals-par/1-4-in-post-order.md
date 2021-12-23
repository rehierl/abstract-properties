
<!-- ======================================================================= -->
# the parent-based encoding, in default post-order

```
       a           default post-order
---------------    ----------------------------------------
 b    c      h     b  d  f  g  e  c  i  h  a - n, nodes
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.id
    d   e    i     9  6  5  5  6  9  8  9  x - d, parent.id
      -----
      f   g
```

Note that these sequences can be formed by the following algorithm.

```js
//- the default post-order traversal
traverseInPreOrder(root) begin
  n=(), r=(), d=()

  visitInPreOrderFTL(node) begin
    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end

    //- visit the current node
    n.append(node)
    node.id = n.length
    r.append(node.id)
  end

  visitInPreOrderFTL(root)

  for (node in n) begin
    d.append(node.parentNode.id)
  end

  return n,r,d
end
```

<!-- ======================================================================= -->
## remarks

Note that, since this traversal will visit a node only after all of its
descendants in the unordered document tree (DTU) have been visited, parent
nodes have in general no id associated once a child is being visited.
To circumvent this issue, a second pass over all the nodes may be used in
order to fill the sequence of parent references.

Note that alternative methods are possible that can be used to circumvent
such a second pass. However, all alternatives have in common that they will
increase the computational complexity in regards to LEVEL, PRE and PRER.
