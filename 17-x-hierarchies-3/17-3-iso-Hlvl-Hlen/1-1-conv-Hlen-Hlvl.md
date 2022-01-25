
# How to transform Hlen into Hlvl

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

Forming a sequence of level values (Hlvl) from a sequence of length values
(Hlen) is in essence a process that decodes Hlvl and one that writes Hlen
without having to actually create the document tree.

Note that the decoding process is used to maintain a rooted path of last index
values `iLast`, which must be reduced if the current index in `len` is about
to pass beyond the `iLast` entries in `rp`. Hence the sequence of level values
can be formed on the fly, without having to recreate the document tree.

```js
//- (Hlen -> Hlvl)
export function convLenToLvl(n, len) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == len.length);
  util.assert(len[0] == num);//- root
  util.assert(len[num-1] == 1);//- leaf
  let rp=[], lvl=[];

  //- read len[], write lvl[]
  for(let i=0; i<num; i++) {
    let count = len[i];
    util.assert(count > 0);
    let iLast = (i+count-1);
    let level = rp.length;

    if(level > 0) {
      let iParent = rp[level-1];
      util.assert(iLast <= iParent);
    }

    rp.push(iLast);
    lvl.push(level+1);

    //- reduce the rooted path
    for(let j=level+1-1; j>=0; j--) {
      if(rp[j] > i) break;
      rp.pop();
    }
  }

  util.assert(rp.length == 0);
  return { n, lvl };
}
```

Note that one does not even have to determine the root nodes.
