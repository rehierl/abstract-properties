
<!-- ======================================================================= -->
# the level-based encoding (LVL)

The following summarizes the sequences produced by the main tree traversal
algorithms when outputting the node level of a node instead of its parent
references. This encoding scheme will be referred to as the
**level-based implicit encoding scheme**.

```
default level-order (LEVEL)                          a
-------------------------------------------   ---------------
a  b  c  h  d  e  i  f  g - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  1  3  3  4  6  6 - par, parent.idx       d   e    i
1  2  2  2  3  3  3  4  4 - lvl, node.lvl           -----
                                                    f   g
default pre-order (PRE)*
-------------------------------------------
a  b  c  d  e  f  g  h  i - n, trace            <-| r
1  2  3  4  5  6  7  8  9 - r, node.idx           | e
x  1  1  3  3  5  5  1  8 - par, parent.idx       | v
1  2  2  3  3  4  4  2  3 - lvl, node.lvl         | e
                                                  | r
reversed pre-order (PRER)*                        | s
-------------------------------------------       | e
a  h  i  c  e  g  f  d  b - n, trace          <-| | d
1  2  3  4  5  6  7  8  9 - r, node.idx         | |
x  1  2  1  4  5  5  4  1 - par, parent.idx     | |
1  2  3  2  3  4  4  3  2 - lvl, node.lvl       | | backward-oriented
                                                | | -----------------
default post-order (POST)                       | | forward-oriented
-------------------------------------------     | |
b  d  f  g  e  c  i  h  a - n, trace          <-| |
1  2  3  4  5  6  7  8  9 - r, node.idx           |
9  6  5  5  6  9  8  9  x - par, parent.idx       |
2  3  4  4  3  2  3  2  1 - lvl, node.lvl         |
                                                  |
reversed post-order (POSTR)                       |
-------------------------------------------       |
i  h  g  f  e  d  c  b  a - n, trace            <-|
1  2  3  4  5  6  7  8  9 - r, node.idx
2  9  5  5  7  7  9  9  x - par, parent.idx
3  2  4  4  3  3  2  2  1 - lvl, node.lvl
```

(*) Note that only the PRE and the PRER encodings are such that they allow to
easily recreate the tree. Even though the POST and POSTR encodings would allow
to recreate the tree at the cost of additional complexity, the LEVEL encoding
can not be relied upon.
