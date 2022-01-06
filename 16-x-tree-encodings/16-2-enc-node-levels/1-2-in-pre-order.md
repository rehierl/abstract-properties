
<!-- ======================================================================= -->
# the level-based encoding, in default pre-order

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
                                                    f   g
```

<!-- ======================================================================= -->
## encoding

Sequences `n` and `lvl` can be formed as follows.

```js
export function encodePRE(root) {
  let n=[], lvl=[];
  let level = 0;

  function visitPreFTL(node) {
    //- enter the node's type-1 scope
    level = (level + 1);

    //- visit the node
    n.push(node.def());
    lvl.push(level);

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);
    }

    //- exit the node's type-1 scope
    level = (level - 1);
  }

  visitPreFTL(root);
  return { n, lvl };
}
```

Note that the level of a node is equal to the number of nodes in its rooted
path, which is why a level value reflects the number of open scopes a the
time a node is being visited. Because of that, the level of a node increases
by one each time a scope is entered, and decreases by one each time a scope
is exited. Consequently, there is no issue when having to determine the level
of a root. That is because one does not require access to a parent object in
order to determine the level of a node.

* `level+1` each time a scope is entered
* `level-1` each time a scope is exited

<!-- ======================================================================= -->
## decoding

The encoded tree can be recreated as follows.

```js
//- assuming `n` is in pre-order
export function decodePRE(n, lvl) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == lvl.length);
  util.assert(lvl[0] == 1);//- a root
  let nodes=[], roots=[], rp=[]
  let last = 0;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes.push(node);

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
    parent.addAsLastChild(node);
  }

  return roots;
}
```

Note that the rooted path `rp` is used as a hashtable. That is, considerations
in regards to some capacity can be ignored at this point.
