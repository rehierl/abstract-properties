
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

Note that the values of the last node indexes are either self-references
(e.g. node `b`) or forward-oriented references (e.g. node `c`). Furthermore,
each pair of first-index and last-index matches the semantics of a pair of
start-tag and end-tag.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lst` can be formed as follows.

```js
//- note - 1/one-based sequences
//- note - 0/zero-based arrays
export function encodePRE(root) {
  let n=[], lst=[];
  //let level = 0;

  function visitPreFTL(node) {
    //- enter the node's type-1 scope
    //level = (level + 1);

    //- visit the node
    n.push(node.def());
    let first = n.length-1;

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);
    }

    //- determine the length
    let last = n.length-1;
    lst[first] = last+1;

    //- exit the node's type-1 scope
    //level = (level - 1);
  }

  visitPreFTL(root);
  return { n, lst };
}
```

Note that a node counter **hashtable** `nc` is not required, since the sequence
of nodes `n` can be understood to do the counting - i.e. `N := (last-first+1)`.
Because of that, there is no need to explicitly count the nodes in `D*(n)`.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in pre-order
export function decodePRE(n, lst) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == lst.length);
  util.assert(lst[0] == len);//- a root
  util.assert(lst[len-1] == len);//- a leaf
  let nodes=[], roots=[], rp=[];

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    nodes.push(current);

    let first = i;
    let last = lst[i]-1;
    util.assert(last >= i);
    util.assert(last < len);

    let count = (last - first + 1);
    current.count = count;
    current.remaining = count;
    let pLen = rp.length;

    if(pLen == 0) {
      roots.push(current);
    }

    if(pLen > 0) {
      let parent = rp[pLen-1];
      util.assert(count <= parent.remaining);
      parent.addAsLastChild(current);
    }

    rp.push(current);
    pLen = rp.length;

    //- first, reduce all node counts
    for(let i=0; i<pLen; i++) {
      rp[i].remaining--;
    }

    //- then, pop entries if necessary
    for(let i=pLen-1; i>=0; i--) {
      if(rp[i].remaining > 0) break;
      rp.pop();
    }
  }

  util.assert(rp.length == 0);
  util.assert(roots.length == 1);
  return roots[0];
}
```

Note that, since the node count can be derived from the current first index
(`i`) and the corresponding last index (`lst[i]`), the decoding algorithm is
a minor modification of the length-based decoding algorithm.
