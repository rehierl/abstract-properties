
<!-- ======================================================================= -->
# the length-based encoding, in default post-order

```
default post-order (POST)                            a
-------------------------------------------   ---------------
b  d  f  g  e  c  i  h  a - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
9  6  5  5  6  9  8  9  x - par, parent.idx       d   e    i
2  3  4  4  3  2  3  2  1 - lvl, node.lvl           -----
1  1  1  1  3  5  1  2  9 - len, node.len           f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `len` can be formed as follows.

```js
export function encodePOST(root) {
  let n=[], len=[];
  //let level = 0;

  function visitPostFTL(node) {
    //- enter the node's type-1 scope
    //level = (level + 1);

    //- keep track of the index of the first
    //  node in the current scope
    //- none of these nodes have been appended to
    //  'n', which is why the first node will be
    //  located at the 0-based index (n.length-1+1)
    let first = (n.length);

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPostFTL(child);
    }

    //- visit the node
    n.push(node.def());
    let last = n.length-1;
    let length = (last - first + 1);
    len.push(length);

    //- exit the node's type-1 scope
    //level = (level - 1);
  }

  visitPostFTL(root);
  return { n, len };
}
```

Note that, compared to the pre-order version, this post-order version is
straight forward since a node and its node count will be appended to the
corresponding sequences once the node's scope is being exited.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in post-order
export function decodePOST(n, len) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == len.length);
  util.assert(len[num-1] == num);//- a root
  util.assert(len[1] == 1);//- a leaf
  let nodes=[], roots=[];
  let rp = new cRootedPath();

  for(let i=num-1; i>=0; i--) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes[i] = node;//- hashtable!

    let count = len[i];
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
