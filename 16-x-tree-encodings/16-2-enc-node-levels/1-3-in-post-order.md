
<!-- ======================================================================= -->
# the level-based encoding, in default post-order

```
default post-order (POST)                           a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lvl` can be formed as follows.

```js
export function encodePOST(root) {
  let n=[], lvl=[];
  let level = 0;

  function visitPostFTL(node) {
    //- enter the node's type-1 scope
    level = (level + 1);

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPostFTL(child);
    }

    //- visit the node
    n.push(node.def());
    lvl.push(level);

    //- exit the node's type-1 scope
    level = (level - 1);
  }

  visitPostFTL(root);
  return { n, lvl };
}
```

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in post-order
export function decodePOST(n, lvl) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == lvl.length);
  util.assert(lvl[len-1] == 1);//- a root
  let nodes=[], roots=[], rp=[]
  let last = 0;

  for(let i=len-1; i>=0; i--) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes[i] = node;//- hashtable!

    let level = lvl[i];
    util.assert(level >= 1);
    node.lvl = level;

    //- assert that the input level does
    //  not exceed the valid range [1,#rp+1]
    util.assert(level <= (last+1));
    rp[level-1] = node;
    last = level;

    //- if the node is a root
    if(level == 1) {
      roots.push(node);
      continue;
    }

    //- the node is a child
    let parent = rp[level-2];
    parent.addAsFirstChild(node);
  }

  return roots;
}
```

Note that, since the ancestors of a node appear subsequent to it, the sequence
of level values must be read in reverse from last to first. That is because
ancestors will then be encountered before any of their descendants. After all,
the tree order is still a suborder to the reversed POST and POSTR traces.

* hence `.addAsFirstChild()`
