
<!-- ======================================================================= -->
# the parent-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

Note that the document tree is such that its nodes are labeled with letters in
ascending order with regards to the pre-order tree traversal. Because of that,
sequence `n` contains the first 9/nine letters in ascending order.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `par` can be formed as follows.

```js
export function encodePRE(root) {
  let n=[], par=[];

  function visitPreFTL(node) {
    //- visit the node
    n.push(node.def());
    node.ref = n.length;

    let parent = node.parentNode;
    let parRef = parent ? parent.ref : 0;
    par.push(parRef);

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);
    }
  }

  visitPreFTL(root);
  return { n, par };
}
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- same as decodeLEVEL()
//- assuming `n` is in pre-order
export function decodePRE(n, par) {
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

Recall that the pre-order tree traversal is backward-oriented. That is, each
node `c` has a parent `p` that is presequent to it in trace `n`. After all,
the tree order is a suborder to the pre-order trace.

* `(p presequent-to c)` is true for `(p ancestor-of c)`
