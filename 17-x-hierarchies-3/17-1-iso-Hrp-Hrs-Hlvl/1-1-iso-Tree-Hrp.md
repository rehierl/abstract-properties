
# the DT-Hrp isomorphism

Forming a sequence of rooted paths from a document tree is straight forward
since one only needs to determine the rooted path of each node while a node
is being visited. It is however more efficient, if the traversal algorithm
updates a stack of nodes with each visit. That is because the current rooted
path will then always be available, without first having to traverse the
ancestors of the current node.

Forming a document tree from a sequence of rooted paths is however a bit more
challenging. That is because one needs to compare the current rooted path with
the previous rooted path. After all, in order to determine the parent of the
node the current rooted path defines, one must **determine the common prefix**
of both paths. That is because the rooted paths of siblings must differ only
in their last nodes.

```js
export function decodeHrp(n, hrp) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == hrp.length);
  util.assert(hrp[0].length == 1);
  let nodes=[], roots=[];
  let rp=[], pOld, pCur;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.ref = (i+1);
    nodes.push(current);

    //- pCur must have the current node
    //  as its characteristic element CE
    //- as its last element
    pCur = hrp[i];

    //- if the node is a root
    if(pCur.length == 1) {
      util.assert(pCur[0] == i+1);
      roots.push(current);
      rp.push(current);
      pOld = pCur;
      continue;
    }

    //- reduce the rooted path to those
    //  nodes that are common to both
    //- reduce rp to the shared prefix
    reduceRp(pOld, pCur, rp);
    let pLen = rp.length;

    //- this node must be the path's CE
    //- a reference to the current node
    util.assert(pCur[pLen] == i+1);

    //- the current node's parent is the
    //  last node in the reduced rooted path
    let parent = rp[pLen-1];
    parent.addAsLastChild(current);

    //- 'rp' must now be equal to 'pCur'
    rp.push(current);
    pOld = pCur;
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

The rooted path being maintained is easily reduced to the shared prefix of the
previous rooted path and the current rooted path.

```js
function reduceRp(pOld, pCur, rp) {
  //- determine the length of the shared prefix
  let pLen = lengthOfPrefix(pOld, pCur);

  //- 'rp' must still be equal to 'pOld'
  util.assert(rp.length == pOld.length);

  //- reduce 'rp' to the prefix of both
  while(rp.length > pLen) {
    rp.pop();
  }

  //- 'pCur' must now have one node on
  //  top of those in the shared prefix
  util.assert(pLen == pCur.length-1);
}
```

Note that forming a document tree (DT) from a hierarchy of rooted paths (Hrp)
is a **backwards-oriented** process. That is, given a current rooted path, the
alogrithm knows the node it represents (i.e. its last node). However, in order
to determine the parent of that node, one needs to know to the previous path.

Note that the previous rooted path may or may not be the rooted path of the
parent of the current node. Likewise, the previous path may or may not be the
rooted path of the next presequent sibling. However, that path may also be any
descendant of the next presequent sibling.
