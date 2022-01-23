
# the DT-Hlvl isomophism

As before, forming a sequence of level values is as straight forward as forming
a sequence of rooted paths. That is because one can easily determine the level
of the current node from the rooted path one maintains. After all, the level
value is the node-length of that path.

Forming a document tree from a sequence of level values is once again a bit
more challenging. However, since the current rooted path must share a common
prefix with the previous rooted path, and since the current rooted path must
only have its last node (i.e. its CE) in addition to that prefix, the level
value from the current node defines the length of that prefix. In combination
with the rooted path being maintained, one can thus easily tell the parent
of the current node.

```js
export function decodeHlvl(n, lvl) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == lvl.length);
  util.assert(lvl[0] == 1);//- a root
  let nodes=[], roots=[], rp=[];
  let last = 0;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes.push(node);

    let level = lvl[i];
    util.assert(level >= 1);
    node.lvl = level;

    //- if the node is a root
    if(level == 1) {
      roots.push(node);
      rp[0] = node;
      last = level;
      continue;
    }

    //- the input level must not
    //  exceed the valid range [1,#rp+1]
    util.assert(level <= (last+1));
    rp[level-1] = node;

    //- the node is a child
    let parent = rp[level-2];
    parent.addAsLastChild(node);

    last = level;
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```
