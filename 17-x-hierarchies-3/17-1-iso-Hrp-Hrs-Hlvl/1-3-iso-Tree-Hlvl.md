
# the DT-Hlvl isomophism

As before, forming a sequence of level values is as straight forward as forming
a sequence of rooted paths. That is because one can easily determine the level
of the current node from the current rooted. After all, the level value is the
node-length of that path.

Forming a document tree from a sequence of level values is once again a bit
more challenging. However, since the current rooted path must share a common
prefix with the previous rooted path, and since the current rooted path must
only have its last node (i.e. its CE) in addition to that prefix, the level
of the current node can be understood to define the length of that prefix.
In combination with the current rooted path, one can thus easily tell the
parent of the current node.

```js
//- (Hlvl -> Tree)
export function decodeHlvl(n, lvl) {
  let len = n.length;
  util.assert(0 < len);
  util.assert(len == lvl.length);
  util.assert(lvl[0] == 1);//- a root
  let nodes=[], roots=[];
  let rp=[], level, last;

  for(let i=0; i<len; i++) {//- i in [0,#n)
    let node = new cNode(n[i]);
    nodes.push(node);

    level = lvl[i];
    util.assert(level >= 1);
    node.lvl = level;

    //- if the node is a root
    if(level == 1) {
      roots.push(node);
      util.assert(rp.length == 0);
      rp.push(node);
      last = level;
      continue;
    }

    //- the input level must not exceed
    //  the valid range [1,#rp+1]
    util.assert(level <= rp.length+1);

    //- reduce rp to the shared prefix
    let pLen = reduceRp(last, level, rp);

    //- the node is a child
    let parent = rp[pLen-1];
    parent.addAsLastChild(node);

    //- 'rp' is now the rooted path
    //  of the current node
    rp.push(node);
    last = level;
    continue;
  }

  util.assert(roots.length == 1);
  return roots[0];
}
```

The current rooted path is easily reduced to the prefix that is shared between
the rooted path of the previous node and the rooted path of the current node.
That is because the level of the current node is the level value of the last
node in the rooted path (its parent node) plus one.

```js
function reduceRp(last, level, rp) {
  //- 'rp' is still the rooted path
  //  of the previous node
  util.assert(rp.length == last);

  //- reduce 'rp' to the shared prefix
  while(rp.length >= level) {
    rp.pop();
  }

  //- the current rooted path must now have
  //  one node on top of those in 'rp'
  util.assert(rp.length == level-1);
  return (level-1);
}
```
