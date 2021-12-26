
<!-- ======================================================================= -->
# the parent-based encoding, in level order

```
default level-order (LEVEL)                         a
-----------------------------------------    ---------------
a  b  c  h  d  e  i  f  g - n, trace          b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx          -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx      d   e    i
                                                   -----
                                                   f   g
```

Recall that a level-order trace can be described as a sequence of child orders,
which is why each child order is a substring to the corresponding trace of
nodes.

Note that the first node of a default level-order trace is always the tree's
root. In contrary to that, the last node of such a trace is not necessarily
a descendant of the root's last child. That is because the last node may be
a descendant of any child of tree's root.

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
encode(root) begin
  next = new Queue()
  next.enqueue(root)
  n=(), r=(), par=()

  while (next.isEmpty() == false) begin
    //- pop the node from the front
    node = next.dequeue()

    //- visit the current node
    n.append(node)

    node.idx = n.length
    r.append(node.idx)

    parRef = node.parentNode.idx
    par.append(parRef)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      //- append the node to the end
      next.enqueue(child)
    end
  end

  //- sequences n,r,par are now complete
  //- sequence 'r' is not required
  return n,par
end
```

Note that the expression `n.append(node)` must be understood such that some
node definition is appended to sequence `n`, rather than an actual node object.
This definition can then be used to recreate each node using expressions such
as `new Node(n[i])` - see below.

Note that the expression `node.idx = n.length` is used to associate the 1-based
index value as a new property to the corresponding node object. Based on that,
and given a node, one can retrieve the value of the node's parent reference.

Note that this JavaScript-based approach is used by the above pseudocode for
its simplcitiy. A clean approach would require to store object-to-value pairs
in a separate hashtable since the corresponding values will then be dropped
automatically, once the encoding process is done.

Note that the document tree's root obviously has no parent of its own. Hence,
the `node.parentNode.idx` line will usually trigger an error. As a matter of
clarity, this line is kept as is.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[1] <= 0)
  nodes=(), roots=()

  for (i=1 to #n) begin
    //- use the node definitions in 'n'
    //  to create actual node objects
    current = new Node(n[i])
    nodes.add(current)
    parRef = par[i]

    if (parRef <= 0) begin
      //- an invalid parent reference
      //- treat the current node as a root
      roots.add(current)
      continue
    end

    if (parRef > #n) or (parRef >= i) begin
      //- the parent reference of the current node
      //  is forward-oriented, which indicates a
      //  serious input error, or a cyclic graph
      assert(false)
    end

    //- (parRef in (0,i)) is guaranteed to be true
    //- the first reference must have been invalid
    parent = nodes[parRef]

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
