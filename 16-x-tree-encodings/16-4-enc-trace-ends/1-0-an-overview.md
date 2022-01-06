
<!-- ======================================================================= -->
# the end-based encoding (END)

The following summarizes the sequences produced by the main tree traversal
algorithms when outputting the index of the first/last node in the trace of
a node. This encoding scheme will be referred to as
**the end-based implicit encoding scheme**.

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
9  1  5  2  1  3  1  1  1 - len, node.len           f   g
x  x  x  x  x  x  x  x  x - end, node.end

default pre-order (PRE)
-------------------------------------------
a  b  c  d  e  f  g  h  i - n, trace
1  2  3  4  5  6  7  8  9 - r, node.idx
x  1  1  3  3  5  5  1  8 - par, parent.idx
1  2  2  3  3  4  4  2  3 - lvl, node.lvl
9  1  5  1  3  1  1  2  1 - len, node.len
9  2  7  4  7  6  7  9  9 - lst, node.lst

reversed pre-order (PRER)
-------------------------------------------
a  h  i  c  e  g  f  d  b - n, trace
1  2  3  4  5  6  7  8  9 - r, node.idx
x  1  2  1  4  5  5  4  1 - par, parent.idx
1  2  3  2  3  4  4  3  2 - lvl, node.lvl
9  2  1  5  3  1  1  1  1 - len, node.len
9  3  3  7  7  6  7  8  9 - lst, node.lst

default post-order (POST)
-------------------------------------------
b  d  f  g  e  c  i  h  a - n, trace
1  2  3  4  5  6  7  8  9 - r, node.idx
9  6  5  5  6  9  8  9  x - par, parent.idx
2  3  4  4  3  2  3  2  1 - lvl, node.lvl
1  1  1  1  3  5  1  2  9 - len, node.len
1  2  3  4  3  2  7  7  1 - fst, node.fst

reversed post-order (POSTR)
-------------------------------------------
i  h  g  f  e  d  c  b  a - n, trace
1  2  3  4  5  6  7  8  9 - r, node.idx
2  9  5  5  7  7  9  9  x - par, parent.idx
3  2  4  4  3  3  2  2  1 - lvl, node.lvl
1  2  1  1  3  1  5  1  9 - len, node.len
1  1  3  4  3  6  3  8  1 - fst, node.fst
```

Note that encoding and decoding algorithms are provided as follows.

```
-      | LEVEL  | PRE    | PRER   | POST   | POSTR
---------------------------------------------------
encode | N.A.   | O(N)   | -      | O(N)   | -
decode | N.A.   | O(N)   | -      | O(N)   | -
```

Note that neither an encoding nor a decoding algorithm can be provided for the
level-order tree traversal. That is because the trace of a node is in general
no substring to the level-order trace of a tree.
