
# How to transform Hlvl into Hlen

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
0  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
9  2  7  4  7  6  7  9  9 - lst, node.lst
-------------------------------------------
               6  7       - lv-4
         4  5  5  5     9 - lv-3
   2  3  3  3  3  3  8  8 - lv-2
1  1  1  1  1  1  1  1  1 - lv-1
0  1  2  3  4  5  6  7  8 - index
```

Note that the tree's pre-order trace covers the top-most nodes of the sequence
of rooted paths. That is, one can visually (i.e. literally) read the sequence
of pre-order traces from the sequence of rooted paths (of node references)
visualized above.

Similar to forming Hlvl from Hlen, forming a sequence of length values (Hlen)
from a sequence of level values (Hlvl) is a process that decodes Hlvl and one
that writes Hlen without having to actually create the document tree.

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
