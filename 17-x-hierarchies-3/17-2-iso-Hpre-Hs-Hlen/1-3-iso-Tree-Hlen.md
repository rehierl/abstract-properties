
# the DT-Hlen isomorphism

Forming a sequence of length values is almost straight forward if one recalls
that each trace is a substring to the traces of its ancestors. Because of that,
each trace can be described in terms of a pair of min-max values, which defines
the first index and the last index in the document tree's pre-order trace.

```js
//- (Tree -> Hlen)
export function encodeHlen(root) {
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

Forming a document tree from a sequence of length values is once again a bit
more challenging. That is because the current rooted path can not be easily as
maintained as before. After all, there are no explicit items (traces or sets)
which can be used to determine the parent of the current node. However, that
relationship can be determined based on the last index values of each trace.

```js
//- (Hlen -> Tree)
export function decodeHlen(n, len) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == len.length);
  util.assert(len[0] == num);//- a root
  util.assert(len[num-1] == 1);//- a leaf
  let nodes=[], roots=[], rp=[];

  for(let i=0; i<num; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.iFirst = i;//- the offset
    nodes.push(current);

    let count = len[i];
    util.assert(count > 0);
    current.iCount = count;

    let iLast = (i+count-1);
    current.iLast = iLast;
    let level = rp.length;

    if(level == 0) {
      roots.push(current);
      rp.push(current);
      reduceRp(i, rp);
      continue;
    }

    if(level > 0) {
      let parent = rp[level-1];
      //- recall the DI-RE case for scopes
      util.assert(iLast <= parent.iLast);
      parent.addAsLastChild(current);
    }

    rp.push(current);
    reduceRp(i, rp);
  }

  util.assert(rp.length == 0);
  util.assert(roots.length == 1);
  return roots[0];
}
```

Note that this decoding algorithm is unique insofar as the rooted path will be
reduced as a last step of each iteration. This is unlike every other decoding
algorithm in which the current rooted path is reduced before pushing the
current node onto that path.

Note that the other decoding algorithms can determine the parent of a current
node only based on the information the next node provides. In contrary to that,
and with this decoding algorithm, one can determine the parent of the next node
before that node is being visited. That is because one can detect if the scope
of a node in the rooted path will be exited - i.e. if the index of the next
node will be outside. Because of that, the rooted path of this decoding
algorithm will always be empty once all nodes have been processed.

```js
function reduceRp(i, rp) {
  for(let j=rp.length-1; j>=0; j--) {
    let node = rp[j];
    //- the node's scope has not been
    //  exited yet - i.e. not yet done
    if(node.iLast > i) break;
    rp.pop();
  }
}
```
