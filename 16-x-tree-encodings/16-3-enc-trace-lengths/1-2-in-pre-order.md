
<!-- ======================================================================= -->
# the length-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
```

<!-- ======================================================================= -->
## encoding (v1)

Sequences `n` and `len` can be formed as follows.

```js
export function encodePREv1(root) {
  let n=[], len=[], nc=[];
  let level = 0;

  function visitPreFTL(node) {
    //- enter the node's type-1 scope
    level = (level + 1);

    //- visit the node
    n.push(node.def());
    let first = n.length-1;

    //- initialize the counter for the current
    //  node - by including/counting itself
    nc[level] = 1;

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);

      //- add the number of nodes of the
      //  induced subtree T[child] to the
      //  node count of the current node
      nc[level] = nc[level] + nc[level+1];
    }

    //- replace the initial node count
    let length = nc[level];
    len[first] = length;

    //- exit the node's type-1 scope
    level = (level - 1);
  }

  visitPreFTL(root);
  return { n, len };
}
```

Note that **a hashtable** of offset values `rp` (read as "rooted path") is
used to maintain the offset indexes of the nodes in the current rooted path.
Likewise, a hashtable of counter values `nc` (read as "node count") is used
to sum up the node count of each node.

Note that the post-order version is straight forward since the node count of
a node will be available when the node and its node count need to be appended
to the corresponding sequences. In contrary to that, this pre-order version
requires to memorize the index of a node such that its initialized node count
can be replaced by the final value.

Note that the above pseudocode incorporates aspects of a pre-order, aspects of
an in-order and also aspects of a post-order traversal. That is because some
operations must be executed before the visit of its first child, some during
the visit of its child nodes, and some after the visit of its last child.

<!-- ======================================================================= -->
## encoding (v2)

Sequences `n` and `len` can be formed as follows.

```js
export function encodePREv2(root) {
  let n=[], len=[];
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
    let length = (last - first + 1);
    len[first] = length;

    //- exit the node's type-1 scope
    //level = (level - 1);
  }

  visitPreFTL(root);
  return { n, len };
}
```

Note that one is in general not required to explicitly count the nodes. That
is because the final length of a trace can be derived from the index of its
first node and the index of its last node.

* `length = (last - first + 1)`

Note that the index of the first node is held by a local variable, that is
maintained on the inner function's local stack. If one would want to implement
this encoding in a non-recursive fashion, one would have to use an explicit
stack (i.e. a rooted path) of offsets.

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in pre-order
export function decodePRE(n, len) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == len.length);
  util.assert(len[0] == num);//- a root
  util.assert(len[num-1] == 1);//- a leaf
  let nodes=[], roots=[], rp=[];

  for(let i=0; i<num; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    nodes.push(current);//- hashtable!

    let count = len[i];
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

Recall that the scope of a node and its pre-order trace have the same sets of
nodes. Because of that, the scope of a node can be described to appear as a
substring to the document tree's pre-order trace `n`. Hence, the length value
of a node `x` is equal to the length of the node's pre-order trace `pre(x)`.

* `pre(x) := n[i,i+N-1]` is true assuming ..
* `(n[i] == x)` and `(len[i] == N)` for `(i in [1,#len])`

Note that the first length entry must be equal to the length of the sequence
of length values - i.e. `(len[1] == #len)`. That is because the scope of a
root includes all the nodes. Likewise, the last entry must have a value of
one - i.e. `(len[#len] == 1)`. That is because the scope of a leaf only
contains the leaf itself.

Note that, due to the entry assertions, the above pseudocode is artificially
reduced to a single tree. That is, the 2nd and 3rd entry assertions must be
altered or dropped if the sequence of length values defines the structure of
a forest of trees. That is because no length value can then be equal to the
length of the sequence of length values.
