
<!-- ======================================================================= -->
# the parent-based encoding, in reversed post-order

```
reversed post-order (POSTR)                          a
-------------------------------------------   ---------------
i  h  g  f  e  d  c  b  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
2  9  5  5  7  7  9  9  x - par, parent.idx       d   e    i
                                                    -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `par` can be formed as follows.

```js
export function encodePOSTR(root) {
  let nodes=[], n=[], par=[];

  function visitPostLTF(node) {
    //- visit the child nodes
    for(let child of node.childNodesLTF) {
      visitPostLTF(child);
    }

    //- visit the node
    nodes.push(node);
    n.push(node.def());
    node.ref = n.length;
  }

  visitPostLTF(root);
  let len = nodes.length;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let parent = nodes[i].parentNode;
    let parRef = parent ? parent.ref : len+1;
    par.push(parRef);
  }

  return { n, par };
}
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in reversed post-order
export function decodePOSTR(n, par) {
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
    parent.addAsLastChild(node);
  }

  return roots;
}
```

Note that, as above, this decoding algorithm would only differ from the
algorithm of the default traversal (POST) in the expression that adds the
current node as a child to its parent.

* note - `.addAsLastChild()` instead of `.addAsFirstChild()`
