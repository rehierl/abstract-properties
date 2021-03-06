
# the Dt-Hrs isomorphism

Forming a sequence of reversed scopes from a document tree is straigt forward.
After all, the reversed scope of each node is equal to the set of nodes in
each rooted path.

Forming a document tree from a sequence of reversed scopes is however a bit
more challenging. After all, each reversed scope, as a simple set of nodes,
does not allow to easily determine the node it represents (i.e. its CE). That
is, if one ignores that each such scope must appear at a particular position
in the sequence of reversed scopes. Other than that, this process is quite
similar to forming a document tree from its sequence of rooted paths.

```js
//- (Hrs -> Tree)
export function decodeHrs(n, hrs) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == hrs.length);
  util.assert(hrs[0].size == 1);
  let nodes=[], roots=[];
  let rp=[], sOld, sCur;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.ref = (i+1);//- 1-based
    nodes.push(current);
    sCur = hrs[i];

    //- sCur must have the current node
    //  as its characteristic element CE
    util.assert(sCur.has(i+1));

    //- if the node is a root
    if(sCur.size == 1) {
      roots.push(current);
      rp.push(current);
      sOld = sCur;
      continue;
    }

    //- reduce rp to the shared subset
    let pLen = reduceRp(sOld, sCur, rp);

    //- get the CE of sCur
    //- must be equal to the current node
    let ceRef = getCeRef(sOld, sCur);
    util.assert(ceRef == i+1);

    //- the current node's parent is the
    //  last node in the reduced rooted path
    let parent = rp[pLen-1];
    parent.addAsLastChild(current);

    //- E(rp) is now equal to 'sCur'
    rp.push(current);
    sOld = sCur;
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

As before one needs to first determine the parent of the current node. This
is first and foremost done by maintaining a rooted path (i.e. `rp`). However,
since the input sequence consists of only simple sets, one needs to recall
that the shared prefix between the current rooted path and the previous rooted
path consists of those nodes that are common to both reversed scopes.

```js
function reduceRp(sOld, sCur, rp) {
  //- E(rp) must still be equal to 'sOld'
  util.assert(rp.length == sOld.size);

  //- count the number of shared nodes
  let pLen = 0;

  for(let e of sOld) {
    if(sCur.has(e)) pLen++;
  }

  //- reduce E(rp) to the common subset
  while(rp.length > pLen) {
    rp.pop();
  }

  //- 'sCur' must now have one node on
  //  top of those in the shared subset
  util.assert(pLen == sCur.size-1);
  util.assert(pLen == rp.length);
  return pLen;
}
```

Once the rooted path has been reduced, the current node must be pushed on top
of it. If one ignores the position of each reversed scope in Hrs, one can still
determine the node the current reversed scope represents. That is because the
characteristic element (CE) of that scope is then the only node *not* in the
shared prefix.

```js
function getCeRef(sOld, sCur) {
  let ce=null, num=0;

  for(let e of sCur) {
    //- if 'e' is in sOld, then 'e' is
    //  an ancestor to the current node
    if(sOld.has(e)) continue;
    //- otherwise, 'e' is the CE of sCur
    ce=e, num++;
  }

  //- error if not exactly one CE
  util.assert(num == 1);
  return ce;
}
```
