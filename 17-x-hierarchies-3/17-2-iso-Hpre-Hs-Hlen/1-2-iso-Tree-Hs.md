
# the DT-Hs isomorphism

Forming a sequence of scopes from a document tree is almost identical to
forming a sequence of pre-order traces. The only difference is that one
maintains a rooted path of simple sets, each of which must be extended by
the node that is being visited.

Likewise, forming a document tree from a sequence of scopes differs first
and foremost in regards to the elements in the current rooted path. Because
of that, the main difference to the decoding algorithm for a hierarchy of
traces are the operations used to reduce the rooted path in order to determine
the parent of the current node.

Note that the characteristic element (CE) of the current scope can not be
easily determined. That is because one would have to know all of the subsets
of that scope, which are unavailable while the scope of the current node is
being processed. That is, the orientation of scopes in the context of the
decoding algorithm (in pre-order) are **forwards-oriented** and thus to some
extent against the general processing order - since the knowledge that is
available at a certain point in time is defined by past events, not by future
events.

```js
//- (Hs -> Tree)
export function decodeHs(n, hs) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == hs.length);
  let all = hs[0];//- the root's scope
  util.assert(all.size == len);
  let nodes=[], roots=[];
  let rp=[], scope;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let current = new cNode(n[i]);
    current.ref = (i+1);
    nodes.push(current);

    //- sCur must have the current node
    //  as its characteristic element CE
    scope = hs[i];
    util.assert(scope.size > 0);
    util.assert(scope.has(i+1));
    current.scope = scope;

    //- reduce the rooted path
    let pLen = reduceRp(scope, rp);

    //- if the node is a root
    if(pLen == 0) {
      roots.push(current);
      rp.push(current);
      continue;
    }

    //- the current node is a child to the
    //  last node in the rooted path
    let parent = rp[pLen-1];
    parent.addAsLastChild(current);
    rp.push(current);
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

As before, all the nodes must be removed from the rooted path which have a
scope (sPar) that is no super-set to the scope (sCur) of the current node.

```js
function reduceRp(sCur, rp) {
  while(true) {
    //- the current node is a root,
    //  if the rooted path is empty
    let len = rp.length;
    if(len == 0) return 0;

    //- test if the current last node
    //  is the current node's parent
    //- sCur must be a subset to sPar
    let parent = rp[len-1];
    let sPar = parent.scope;
    let result = isSubsetOf(sPar, sCur);

    //- if yes, then that last node
    //  is the current node's parent
    if(result == true) return len;

    //- if not, then the scope of that last
    //  node has ended - hence, pop that node
    rp.pop();
  }
}
```
