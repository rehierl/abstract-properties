
# the DT-Hrp isomorphism

Forming a sequence of rooted paths from a document tree is straight forward
since one only needs to determine the rooted path of each node. It is however
more efficient, if the traversal algorithm maintains a stack of nodes, which
represents the current rooted path. That is because the current rooted path
will then always be available, without first having to traverse the ancestors
of the current node.

```js
//- (Tree -> Hrp)
export function encodeHrp(root) {
  let n=[], hrp=[];
  let rp=[], path;

  //- clone the current rooted path
  function clone(rp) {
    let path = new Array();
    for(let node of rp) {
      path.push(node.ref);
    }
    return path;
  }

  function visitPreFTL(node) {
    //- enter the node's type-1 scope
    rp.push(node);

    //- visit the current node
    n.push(node.def());
    node.ref = n.length;
    path = clone(rp);
    hrp.push(path);

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);
    }

    //- exit the node's type-1 scope
    rp.pop();
  }

  visitPreFTL(root);
  return { n, hrp };
}
```

Forming a document tree from a sequence of rooted paths is however a bit more
challenging. That is because one needs to compare the current rooted path with
the previous rooted path. After all, in order to determine the parent of the
current node, one must **determine the common prefix** of both paths.

Recall that the rooted paths of siblings share a common prefix and only differ
in their last nodes.

```js
//- (Hrp -> Tree)
export function decodeHrp(n, hrp) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == hrp.length);
  util.assert(hrp[0].length == 1);
  let nodes=[], roots=[];
  let rp=[], pOld, pCur;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.ref = (i+1);//- 1-based
    nodes.push(current);
    pCur = hrp[i];

    //- pCur must have the current node
    //  as its characteristic element (CE)
    util.assert(pCur[pCur.length-1] == (i+1));

    //- if the node is a root
    if(pCur.length == 1) {
      roots.push(current);
      rp.push(current);
      pOld = pCur;
      continue;
    }

    //- reduce rp to the shared prefix
    let pLen = reduceRp(pOld, pCur, rp);

    //- the current node's parent is the
    //  last node in the shared prefix
    let parent = rp[pLen-1];
    parent.addAsLastChild(current);

    //- 'rp' is now equal to 'pCur'
    rp.push(current);
    pOld = pCur;
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

The rooted path being maintained is easily reduced to the prefix that is shared
between the previous rooted path and the current rooted path.

```js
function reduceRp(pOld, pCur, rp) {
  //- 'rp' must still be equal to 'pOld'
  util.assert(util.cmpArrays(rp, pOld) == 0);

  //- determine the length of the shared prefix
  let pLen = lengthOfPrefix(pOld, pCur);

  //- reduce 'rp' to the prefix of both
  while(rp.length > pLen) {
    rp.pop();
  }

  //- 'pCur' must now have one node on
  //  top of those in the shared prefix
  util.assert(pLen == rp.length);
  util.assert(pLen == pCur.length-1);
  return pLen;
}
```

Note that forming a document tree (DT) from a hierarchy of rooted paths (Hrp)
is a **backwards-oriented** process. That is because in order to determine the
parent of the current node, one needs to know to the previous rooted path.

Note that the previous rooted path may or may not be the rooted path of the
parent of current node's parent. Likewise, the previous path may or may not be
the rooted path of the next presequent sibling. However, that path may also be
any descendant of the next presequent sibling.
