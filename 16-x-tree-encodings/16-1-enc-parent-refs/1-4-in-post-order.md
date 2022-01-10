
<!-- ======================================================================= -->
# the parent-based encoding, in default post-order

```
default post-order (POST)                            a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `par` can be formed as follows.

```js
export function encodePOST(root) {
  let nodes=[], n=[], par=[];

  function visitPostFTL(node) {
    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPostFTL(child);
    }

    //- visit the node
    nodes.push(node);
    n.push(node.def());
    node.ref = n.length;
  }

  visitPostFTL(root);
  let len = nodes.length;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let parent = nodes[i].parentNode;
    let parRef = parent ? parent.ref : len+1;
    par.push(parRef);
  }

  return { n, par };
}
```

Note that, since this traversal will visit a node after all of its descendants
(in DTU) have been visited, parent nodes have no index associated while a child
is being visited. To circumvent this issue, a second pass over all the nodes
is used in order to first determine all the node references.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in post-order
export function decodePOST(n, par) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == par.length);
  util.assert(par[len-1] >= len);//- a root
  let nodes=[], roots=[];

  for(let i=len-1; i>=0; i--) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes[i] = node;//- hashtable!
    let ref = par[i];

    //- a root
    if(ref > len) {
      roots.push(node);
      continue;
    }

    //- invalid reference
    if(ref <= 0) {
      util.assert(false);
    }

    //- a cyclic graph
    if((ref-1) <= i) {
      util.assert(false);
    }

    //- (ref-1) in (i,#n)
    let parent = nodes[ref-1];
    parent.addAsFirstChild(node);
  }

  return roots;
}
```

Recall that the post-order tree traversal is forward-oriented. That is, each
node `c` has a parent `p` that is subsequent to it in trace `n`.

* `(p subsequent-to c)` is true for `(p ancestor-of c)`

Note that, even though the tree order is no suborder to the post-order trace,
it still is a suborder to the reversed trace. However, the doctree's child
order is still a suborder to the post-order trace.

Note that, in the context of a forward-oriented encoding, the value of an
invalid reference (x) is assumed to have the non-constant value `#n+1`.
