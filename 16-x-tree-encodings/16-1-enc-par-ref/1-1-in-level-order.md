
<!-- ======================================================================= -->
# the parent-based encoding, in level order

```
       a           level-order
---------------    ----------------------------------------x
 b    c      h     a  b  c  h  d  e  i  f  g - n, trace
    -----   ---    1  2  3  4  5  6  7  8  9 - r, node.idx
    d   e    i     x  1  1  1  3  3  4  6  6 - d, parent.idx
      -----
      f   g
```

<!-- ======================================================================= -->
## encoding

The above sequences can be formed by the following algorithm.

```js
encode(root) begin
  next = new Queue()
  next.enqueue(root)
  n=(), r=(), d=()

  while (next.isEmpty() == false) begin
    //- pop the node from the front
    node = next.dequeue()

    //- visit the current node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
    d.append(node.parentNode.idx)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      //- append the node to the end
      next.enqueue(child)
    end
  end

  //- sequences n,r,d are now complete
  //- sequence 'r' is not required
  return n,d
end
```

Note that the expression `node.idx = n.length` is used to associate the
reference value of the current node with its node object. Based on that,
and given the node object, one can retrieve the value of the corresponding
reference.

Note that this approach is used by the above pseudocode for its simplcitiy.
A clean approach would however require to store object-to-value pairs in a
separate hashtable since the corresponding values would then be automatically
dropped once the encoding process is done.

Note that the document tree's root obviously has no parent of its own. Hence,
the `d.append(node.parentNode.idx)` line will usually trigger an error. As a
matter of clarity, this line is kept as is.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, d) begin
  assert((0 < #n) and (#n == #d))
  assert(d[1] <= 0)
  nodes=(), roots=()

  for (i=1 to #n) begin
    //- use the node definitions in 'n'
    //  to create actual node objects
    current = new Node(n[i])
    nodes.add(current)
    parentRef = d[i]

    if (parentRef <= 0) begin
      //- an invalid parent reference
      //- treat the current node as a root
      roots.add(current)
      continue
    end

    if (parentRef > #n) or (parentRef >= i) begin
      //- the parent reference of the current node
      //  is forward-oriented, which indicates a
      //  serious input error, or a cyclic graph
      assert(false)
    end

    //- (parentRef in (0,i)) is guaranteed to be true
    //- the first reference must have been invalid
    parent = nodes[parentRef]

    //- add the current node as a child to the end
    //  of the parent's list of child nodes
    parent.addAsLastChild(current)
  end

  //- (#roots > 0) is true
  return roots
end
```

Note that, since the level-order trace of a document tree can be described
as a sequence of disjoint child orders, certain improvements are obviously
possible. However, the point of this discussion is, at this point not on
highly efficient implementations, which is why the above pseudocode is
identical to that of the pre-order traversal.

Note that the first index of an array in a real-world implementation has
in general a value of 0/zero - i.e. a zero-based arrays. However, in this
discussion, any index-order is assumed to have an index value of 1/one as
its first index - i.e. one-based sequences. Based on that, the invalid
reference (x) is assumed to be 0/zero (or negative).
