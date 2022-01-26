
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
visual: hierarchy of rooted paths (hrp)
visual: rooted paths of node references
               6  7       - lv-4
         4  5  5  5     9 - lv-3
   2  3  3  3  3  3  8  8 - lv-2
1  1  1  1  1  1  1  1  1 - lv-1
0  1  2  3  4  5  6  7  8 - index
-------------------------------------------
visual: hierarchy of traces (hlvl)
               6  7       - lv-4
         4  5======     9 - lv-3
   2  3============  8=== - lv-2
1======================== - lv-1
0  1  2  3  4  5  6  7  8 - index
-------------------------------------------
visual: rooted path of updated node counts
               1  1       - lv-4
         1  3  2  1     1 - lv-3
   1  5  4  3  2  1  2  1 - lv-2
9  8  7  6  5  4  3  2  1 - lv-1
0  1  2  3  4  5  6  7  8 - index
```

Note that the document tree's trace covers the top-most nodes of the sequence
of rooted paths (of node references). One can therefore visually "see" the
sequence of traces in the sequence of rooted paths. That is because the
reference of a node becomes part of a rooted path at the node's node level
as soon as the node's scope is entered. Likewise, the node reference remains
part of all subsequent rooted paths until the node's scope has been exited.

# meta, next-level

an order-preserving tree traversal must be used
- no operation executed while traversing a tree
  may produce conflicting results

child order
- include the parent as a first node ?
- seems to more closely match the concept of scopes
- seems to cause issues when forming scopes, which
  must not contain the parent/defining node
- still more similar to A*() and D*()
- see the parent-based encoding

if exit-events of multiple scopes match the same end-tag?
- first close the scope with the last defining node?
- issue with different types of sections - section, hx
