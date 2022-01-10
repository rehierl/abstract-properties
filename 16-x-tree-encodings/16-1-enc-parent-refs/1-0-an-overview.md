
<!-- ======================================================================= -->
# the parent-based encoding (PAR)

The following provides an overview of the sequences produced.

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
                                                    -----
default pre-order (PRE)                             f   g
-------------------------------------------
a  b  c  d  e  f  g  h  i - n, trace            <-| r
1  2  3  4  5  6  7  8  9 - r, node.idx           | e
x  1  1  3  3  5  5  1  8 - par, parent.idx       | v
                                                  | e
reversed pre-order (PRER)                         | r
-------------------------------------------       | s
a  h  i  c  e  g  f  d  b - n, trace          <-| | e
1  2  3  4  5  6  7  8  9 - r, node.idx         | | d
x  1  2  1  4  5  5  4  1 - par, parent.idx     | |
                                                | | backward-oriented
default post-order (POST)                       | | -----------------
-------------------------------------------     | | forward-oriented
b  d  f  g  e  c  i  h  a - n, trace          <-| |
1  2  3  4  5  6  7  8  9 - r, node.idx           |
9  6  5  5  6  9  8  9  x - par, parent.idx       |
                                                  |
reversed post-order (POSTR)                       |
-------------------------------------------       |
i  h  g  f  e  d  c  b  a - n, trace            <-|
1  2  3  4  5  6  7  8  9 - r, node.idx
2  9  5  5  7  7  9  9  x - par, parent.idx
```

Note that encoding and decoding algorithms are provided as follows.

```
-      | LEVEL  | PRE    | PRER   | POST   | POSTR
---------------------------------------------------
encode | O(2*N) | O(N)   | O(N)   | O(2*N) | O(2*N)
decode | O(N)   | O(N)   | -      | O(N)   | -
```
