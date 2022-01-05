
<!-- ======================================================================= -->
# the parent-based encoding, in default level-order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

Recall that a level-order trace is such that the child order of each parent is
a substring (i.e. not just a suborder) to the level-order trace, which is why
such a trace can be described as a sequence of child orders.

Note that the first node of a default level-order trace is the tree's root. In
contrary to that, the last node of such a trace is not necessarily a descendant
of the root's last child. That is because the last node may be a descendant of
any node that is a child to tree's root.

<!-- ======================================================================= -->
## encoding

Sequences `n`, `r` and `par` can be formed as follows.

```js
export function encodeLEVEL(root) {
  let next = new cQueue();
  next.enqueue(root);
  let n=[], r=[], par=[];

  while(next.hasNext) {
    let node = next.dequeue();

    //- visit the node
    n.push(node);
    node.ref = n.length;
    r.push(node.ref);

    let parent = node.parentNode;
    let parRef = parent ? parent.ref : 0;
    par.push(parRef);

    //- plan the visit of each child
    for(let child of node.childNodesFTL) {
      next.enqueue(child);
    }
  }

  return { n, par };
}
```

Note that the expression `n.append(node)` must be understood such that some
node definition is appended to sequence `n`, rather than an actual node object.
This definition can then be used to recreate each node using expressions such
as `new Node(n[i])` - see below.

Note that the expression `node.idx = n.length` is used to associate the 1-based
index value as a new property to the corresponding node object. Based on such
a property one can determine the value of the node's parent index/reference.

Note that this JavaScript-based approach is used for its simplcitiy. A better
approach would require to store object-value pairs in a separate hashtable.
That is because the corresponding pairs will then be dropped once the encoding
process is done.

Note that, since sequence `r` will not be returned, subsequent algorithms will
omit this sequence entirely. After all, it merely holds the index values of
the nodes in the order in which they will be appended to sequence `n`.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- same as decodePRE()
//- assuming `n` is in level-order
export function decodeLEVEL(n, par) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == par.length);
  util.assert(par[0] <= 0);//- a root
  let nodes=[], roots=[];

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes.push(node);
    let ref = par[i];

    //- a root
    if(ref <= 0) {
      roots.push(node);
      continue;
    }

    //- invalid reference
    if(ref > n.length) {
      util.assert(false);
    }

    //- a cyclic graph
    if((ref-1) >= i) {
      util.assert(false);
    }

    let parent = nodes[ref-1];
    parent.addAsLastChild(node);
  }

  return roots;
}
```

Note that, since the level-order trace of a document tree can be described as
a sequence of child orders, certain improvements are possible. However, since
the focus of this discussion is on simplicity, not on efficiency, this code
is kept as-is - i.e. **identical to that of the pre-order traversal**.

Note that the first index of an array in a real-world implementation has in
general a value of `0/zero` - i.e. **zero-based arrays**. However, in this
discussion, the index-order of any sequence is assumed to have an index value
of `1/one` as its first index - i.e. **one-based sequences**.

Note that, in the context of a backward-oriented encoding, the value of an
invalid reference (x) is assumed to have a constant value of `0/zero`.
