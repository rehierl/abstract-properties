
<!-- ======================================================================= -->
# the parent-based encoding, in reversed pre-order

```
reversed pre-order (PRER)                            a
-------------------------------------------   ---------------
a  h  i  c  e  g  f  d  b - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  2  1  4  5  5  4  1 - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `par` can be formed as follows.

```js
export function encodePRER(root) {
  let n=[], par=[];

  function visitPreLTF(node) {
    //- visit the node
    n.push(node.def());
    node.ref = n.length;

    let parent = node.parentNode;
    let parRef = parent ? parent.ref : 0;
    par.push(parRef);

    //- visit the child nodes
    for(let child of node.childNodesLTF) {
      visitPreLTF(child);
    }
  }

  visitPreLTF(root);
  return { n, par };
}
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in reversed pre-order
export function decodePRER(n, par) {
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
    parent.addAsFirstChild(node);
  }

  return roots;
}
```

Note that, like the encoding algorithm, the decoding algorithm only differs
from the algorithm of the default traversal (PRE) in the expression that adds
the current node as a child to its parent.

* `.addAsFirstChild()` instead of `.addAsLastChild()`
