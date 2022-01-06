
<!-- ======================================================================= -->
# the end-based encoding, in default post-order

```
default post-order (POST)                            a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
1  1  1  1  3  5  1  2  9 - len, node.len           f   g
1  2  3  4  3  2  7  7  1 - fst, node.fst
```

Note that the index associated with a node marks the index of the first node
of the node's pre-order trace. Hence, **the sequence of end indexes** `end`
will be referred to as **the sequence of first indexes** `fst` in the context
of a post-order tree traversal.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `fst` can be formed as follows.

```js
export function encodePOST(root) {
  let n=[], fst=[];
  let level = 0;

  function visitPostFTL(node) {
    //- enter the node's type-1 scope
    level = (level + 1);

    //- keep track of the index of the first
    //  node in the current scope
    //- none of these nodes have been appended to
    //  'n', which is why the first node will be
    //  located at the 0-based index (n.length-1+1)
    let first = n.length;

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPostFTL(child);
    }

    //- visit the node
    n.push(node.def());
    let last = n.length-1;
    fst[last] = first+1;

    //- exit the node's type-1 scope
    level = (level - 1);
  }

  visitPostFTL(root);
  return { n, fst };
}
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in post-order
export function decodePOST(n, fst) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == fst.length);
  util.assert(fst[len-1] == 1);//- a root
  util.assert(fst[0] == 1);//- a leaf
  let nodes=[], roots=[];
  let rp = new cRootedPath();

  for(let i=len-1; i>=0; i--) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes[i] = node;//- hashtable!

    let first = fst[i]-1;
    let last = i;
    util.assert(first >= 0);
    util.assert(first <= i);
    let count = (last - first + 1);
    rp.push(node, count);

    if(rp.length == 1) {
      roots.push(node);
    }

    if(rp.length > 1) {
      let parent = rp.parentNode;
      parent.addAsFirstChild(node);
    }

    rp.pop();
  }

  util.assert(rp.length == 0);
  return roots;
}
```

Note that, since the node count can be derived from the current last index
(`i`) and the corresponding first index (`fst[i]`), the decoding algorithm
is a minor modification of the length-based decoding algorithm.
