
<!-- ======================================================================= -->
# the parent-based encoding, in level order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

Recall that a level-order trace is such that each child order is a substring
to the trace, which is why such a trace can be described as a sequence of
child orders.

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
    node = next.dequeue()

    //- visit the node
    n.append(node)
    node.idx = n.length
    r.append(node.idx)
    parent = node.parentNode
    parRef = parent ? parent.idx : 0
    par.append(parRef)

    //- plan the visit of each child
    for (child in node.childNodesFTL) begin
      next.enqueue(child)
    end
  end

  return n,par
end
```

Note that the expression `n.append(node)` must be understood such that some
node definition is appended to sequence `n`, rather than an actual node object.
This definition can then be used to recreate each node using expressions such
as `new Node(n[i])` - see below.

Note that the expression `node.idx = n.length` is used to associate the 1-based
index value as a new property to the corresponding node object. Based on that,
and given a node, one can determine the value of the node's parent reference.

Note that this JavaScript-based approach is used by the above pseudocode for
its simplcitiy. A clean approach would require to store object-value pairs
in a separate hashtable since the corresponding values will then be dropped
once the encoding process is done.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
decode(n, par) begin
  assert((0 < #n) and (#n == #par))
  assert(par[1] <= 0)//- must be a root
  nodes=(), roots=()

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)
    parRef = par[i]

    //- a root node
    if (parRef <= 0) begin
      roots.append(node)
      continue
    end

    //- an invalid reference
    if (parRef > #n) begin
      assert(false)
    end

    //- a cyclic graph
    if (parRef >= i) begin
      assert(false)
    end

    //- parRef in [1,i]
    parent = nodes[parRef]
    parent.addAsLastChild(node)
  end

  return roots
end
```

Note that, since the level-order trace of a document tree can be described
as a sequence of child orders, certain improvements are possible. However,
since the point of this discussion is not on efficiency, this pseudocode is
kept **identical to that of the pre-order traversal**.

Note that the first index of an array in a real-world implementation has
in general a value of 0/zero - i.e. zero-based arrays. However, in this
discussion, any index-order is assumed to have an index value of 1/one as
its first index - i.e. one-based sequences.

Note that, in the context of a backward-oriented encoding, the invalid
reference (x) is assumed to have a value of `0/zero`.
