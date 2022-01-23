
# the DT-Hpre isomorphism

Forming a sequence of pre-order traces from a document tree is almost straight
forward since one needs to maintain a rooted path of sequences such that the
next node being visited can be appended to each sequence in it. Once the scope
of a node has been exited, the node's pre-order trace can be written to the
hierarchy of pre-order traces (Hpre) at the corresponding position.

Note that the process of writing a sequence to a position that is presequent to
the position of the current node, will make the process difficult to implement
for very large documents. This aspect can however be ignored, since (A) this
hierarchy is of theoretical nature, and (B) the context of this discussion is
on document trees of limited size. That is, all sequences can be formed and
updated in memory.

```js
export function encodeHpre(root) {
  let n=[], hpre=[], rp=[];

  function visitPreFTL(node) {
    //- enter the node's type-1 scope
    let trace = new Array();
    rp.push(trace);

    //- visit the current node
    n.push(node.def());
    node.ref = n.length;
    hpre.push(null);

    //- append the node reference to each
    //  trace in the current rooted path
    for(let trace of rp) {
      trace.push(node.ref);
    }

    //- visit the child nodes
    for(let child of node.childNodesFTL) {
      visitPreFTL(child);
    }

    //- exit the node's type-1 scope
    trace = rp.pop();
    hpre[node.ref-1] = trace;
  }

  visitPreFTL(root);
  return { n, hpre };
}
```

Forming a document tree from a sequence of pre-order traces is more challenging.
That is because unlike hierarchies of rooted paths, there is no direct method
which would allow to easily maintain a current rooted path. That path however
must be maintained since one must be able to determine the parent of the next
current node.

Recall that the characteristic element (CE) of a pre-order trace is its very
first node. That is, the first node of a trace determines the node that trace
represents. In addition to that, this node must correspond with the position
of a trace in the hierarchy of pre-order traces (Hpre). After all, that
sequence is expected to provide all traces in pre-order.

```js
export function decodeHpre(n, hpre) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == hpre.length);
  let pre = hpre[0];//- the root's trace
  util.assert(pre.length == len);
  util.assert(pre[0] == 1);//- the root
  let nodes=[], roots=[];
  let rp=[], tCur;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.ref = (i+1);
    nodes.push(current);

    //- tCur must have the current node
    //  as its characteristic element CE
    //- as its first element
    tCur = hpre[i];
    util.assert(tCur.length > 0);
    util.assert(tCur[0] == (i+1));
    current.trace = tCur;

    //- reduce the rooted path
    let pLen = reduceRp(tCur, rp);

    //- if the node is a root
    if(pLen == 0) {
      rp.push(current);
      roots.push(current);
      continue;
    }

    //- the current node is a child to the
    //  last node in the rooted path
    let parent = rp[pLen-1];
    parent.addAsLastChild(current);
    rp.push(current);
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

Note that the efficiency of the encoding algorithm can be improved, if the
trace of the node whose scope is being exited, is appended to the next trace
in the rooted path being maintained. In other words, it is not necessary to
append the current node to all the traces in that rooted path.

As before with a hierarchy of rooted paths, the rooted path being maintained
must be reduced such that the resulting path ends in the parent of the current
node/trace. This process is however more or less straight forward since the
current trace must be a substring to the parent's trace. Because of that, all
the nodes whose traces are no super-strings to the current trace need to be
removed from the rooted path being maintained.

```js
function reduceRp(tCur, rp) {
  while(true) {
    //- the current node is a root,
    //  if the rooted path is empty
    let len = rp.length;
    if(len == 0) return 0;

    //- test if the current last node is
    //  an ancestor to the current node
    //- tCur must be a substring to tPar
    let parent = rp[len-1];
    let tPar = parent.trace;
    let offset = indexOf(tPar, tCur);

    //- if yes, then that last node
    //  is the current node's parent
    if(offset > 0) return len;

    //- if not, then the scope of that last
    //  node has ended - hence, pop that node
    rp.pop();
  }
}
```
