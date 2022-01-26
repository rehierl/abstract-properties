
# How to transform Hlvl into Hlen

Similar to forming Hlvl from Hlen, forming a sequence of length values (Hlen)
from a sequence of level values (Hlvl) is the process that decodes Hlvl and
writes Hlen without having to actually create the document tree.

Note that each length entry in `len` must be initialized since the actual
length value will only be available once the type-1 scope of the corresponding
node is being exited. (Recall that each trace is a substring to the traces of
its ancestors).

```js
//- (Hlvl -> Hlen)
export function convLvlToLen(n, lvl) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == lvl.length);
  util.assert(lvl[0] == 1);//- root
  let len=[], rp=[];

  //- read lvl[], write len[]
  for(let i=0; i<num; i++) {
    let level = lvl[i];
    util.assert(level > 0);
    len.push(0);//- init len[i]

    //- reduce the rooted path
    reduceRp(rp, level, len);

    //- push the current level as a child
    util.assert(rp.length == level-1);
    rp.push({ iFirst: i, length: 1 });
    continue;
  }

  reduceRp(rp, 1, len);//- clear
  util.assert(rp.length == 0);
  return { n, len };
}
```

Note that each entry of the current rooted path `rp` is a simple object of two
properties only: (1) an offset `iFirst` of the trace of the corresponding node,
and (2) a current node count `length` which is used to count the nodes in the
corresponding trace.

Note that the rooted path `rp` is iteratively reduced to the prefix that is
shared between the previous node and the current node. Because of that, and at
the very end, the rooted path must be reduced to an empty path. Otherwise, not
all length values would be written to the output sequence `len`.

```js
function reduceRp(rp, level, len) {
  let length = rp.length;

  while(length >= level) {
    let node = rp.pop();
    len[node.iFirst] = node.length;

    length = (length - 1);
    if(length == 0) break;

    //- the current node has a parent
    let parent = rp[length-1];
    parent.length += node.length;
  }
}
```

Note that this version does not increase the node count of each trace in the
rooted path. Instead, the node count of a trace will be increased each time
the type-1 scope of a child has been exited.
