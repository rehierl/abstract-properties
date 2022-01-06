
<!-- ======================================================================= -->
# the length-based encoding, in default level-order

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
9  1  5  2  1  3  1  1  1 - len, node.len           f   g
```

Note that the length values in level-order are not monotone decreasing.

<!-- ======================================================================= -->
## encoding

Sequences `n` and `len` can be formed as follows.

```js
export function encodeLEVEL(root) {
  let n=[], len=[];

  //- recursively determine #D*(n)
  //- used to pre-determine all node counts
  function nodeCountOf(node) {
    //- if the result is already available
    if(node.len !== undefined) {
      return node.len
    }

    //- count the node itself
    let count = 1;

    //- visit all child nodes
    for(let child of node.childNodes) {
      count = count + nodeCountOf(child);
    }

    //- store the result of each node
    node.len = count;
    return count;
  }

  //- traverse the tree in level-order
  function visitLevelFTL(node) {
    let next = new cQueue();
    next.enqueue(root);

    while(next.hasNext) {
      let node = next.dequeue();

      //- visit the node
      n.push(node.def());
      len.push(node.len);

      //- plan the visit of each child
      for(let child of node.childNodesFTL) {
        next.enqueue(child);
      }
    }
  }

  let count = nodeCountOf(root);
  visitLevelFTL(root);

  return { n, len };
}
```

Note that the computational complexity is improved at the cost of increased
storage requirements - i.e. `node.len`. Without that property, the algorithm
would have exponential runtime since one would then have to determine the
node count of each node by traversing the corresponding induced subtree.

<!-- ======================================================================= -->
## decoding

Note that the sequence of length values produced by a level-order traversal
**can not be used to easily decode a document tree**. That is because one
can not reliably tell the parent a node has in the level-order trace.

Note that the node count of a node is such that its value minus one is the
sum of the node counts in one or more child orders. With that in mind one
could imagine a sequence of child orders for which it is not possible to
uniquely resolve such a sum - i.e. there might be more than one possibility.
