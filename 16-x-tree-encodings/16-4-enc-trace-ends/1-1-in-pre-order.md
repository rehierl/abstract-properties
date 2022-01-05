
<!-- ======================================================================= -->
# the end-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
9  2  7  4  7  6  7  9  9 - lst, node.lst
```

Note that the index associated with a node marks the index of the last node
of the node's pre-order trace. Hence, **the sequence of end indexes** `end`
will be referred to as **the sequence of last indexes** `lst` in the context
of a pre-order tree traversal.

Note that the values of the last node indexes are either self-references (e.g.
node `b`) or forward-oriented references (e.g. node `c`). Furthermore, each
pair of first-index and last-index matches the semantics of a pair of start-tag
and end-tag.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lst` can be formed as follows.

```js
encode(root) begin
  n=(), lst=()
  level = 0

  visitInPreOrderFTL(node) begin
    //- enter the node's type-1 scope
    level = (level + 1)

    //- visit the node
    first = (n.length + 1)
    n.append(node)
    lst.append(0)

    //- visit the child nodes
    for (child in node.childNodesFTL) begin
      visitInPreOrderFTL(child)
    end

    //- overwrite the initial last index
    last = n.length
    lst[first] = last

    //- exit the node's type-1 scope
    level = (level - 1)
  end

  visitInPreOrderFTL(root)
  return n,lst
end
```

Note that a node counter **hashtable** `nc` is not required, since the sequence
of nodes `n` can be understood to do the counting - i.e. `N := (last-first+1)`.
Because of that, there is no need to explicitly count the nodes in `D*(n)`.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming 'n' is in pre-order
decode(n, lst) begin
  assert((0 < #n) and (#n == #lst))
  //- assuming a single document tree
  assert(lst[1] == #n)//- must be a root
  assert(lst[#n] == #n)//- must be a leaf
  nodes=(), roots=()
  rp = new RootedPath()

  for (i=1 to #n) begin
    node = new Node(n[i])
    nodes.append(node)

    first = i
    last = lst[i]
    assert(last >= i)
    assert(last <= #n)
    count = (last - first + 1)
    rp.push(node, count)

    if (#rp == 1) begin
      roots.append(node)
    end

    if (#rp > 1) begin
      parent = rp.parent()
      parent.addAsLastChild(node)
    end

    //- reduce the node count of each node
    //  and pop all the nodes that have a
    //  remaining node count of 0/zero
    rp.pop()
  end

  assert(#rp == 0)
  return roots
end
```

Note that, since the node count can be derived from the current first index
(`i`) and the corresponding last index (`lst[i]`), the decoding algorithm is
a minor modification of the length-based decoding algorithm.
