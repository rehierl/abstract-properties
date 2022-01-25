
# the Hpre-Hlen isomorphism

Forming a sequence of length values from a sequence of rooted paths is straight
forward. After all, one only needs to replace each trace by the number of nodes
in it.

```js
//- (Hpre -> Hlen)
export function convHpreToHlen(n, hpre) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == hpre.length);
  util.assert(hpre[0].length == num);//- root
  util.assert(hpre[num-1].length == 1);//- leaf
  let i=0, len=[];

  for(i=0; i<num; i++) {
    let pre = hpre[i];
    util.assert(pre.length > 0);
    len.push(pre.length);
  }

  return { n, len };
}
```

The conversion of a hierarchy of length values into a hierarchy of traces is
just as straight forward. After all, each trace is a substring to the implicit
sequence of node references `r`, which matches the index order of the sequence
of node definitions `n`.

```js
//- (Hlen -> Hpre)
export function convHlenToHpre(n, len) {
  let num = n.length;
  util.assert(0 < num);
  util.assert(num == len.length);
  util.assert(len[0] == num);//- root
  util.assert(len[num-1] == 1);//- leaf
  let hpre=[];

  for(let i=0; i<num; i++) {
    let count = len[i];
    let iLast = (i+count-1);
    util.assert(count > 0);
    util.assert(iLast < num);
    let trace = [];

    //- each trace is a substring
    for(let j=i; j<=iLast; j++) {
      //- push 1-based references
      trace.push(j+1);
    }

    hpre.push(trace);
  }

  return { n, hpre };
}
```

Note that a path-based conversion algorithm would be possible. However, this
version would certainly turn out to be a lot more complex than the above.
