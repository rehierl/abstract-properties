
<!-- ======================================================================= -->
# a visual summary

The following summarizes the sequences produced by the main tree traversal
algorithms in regards to the default parent-based explicit encoding scheme
and in regards to a document tree whose nodes are labeled in pre-order.

The sequences produced of each tree traversal are as follows.

```
default level-order (LVL)                           a
-----------------------------------------    ---------------
a  b  c  h  d  e  i  f  g - n, trace          b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx          -----   ---
x  1  1  1  3  3  4  6  6 - d, parent.idx        d   e    i
                                                   -----
default pre-order (PRE)                            f   g
-----------------------------------------
a  b  c  d  e  f  g  h  i - n, trace           <-| r
1  2  3  4  5  6  7  8  9 - r, node.idx          | e
x  1  1  3  3  5  5  1  8 - d, parent.idx        | v
                                                 | e
reversed pre-order (PRER)                        | r
-----------------------------------------        | s
a  h  i  c  e  g  f  d  b - n, trace         <-| | e
1  2  3  4  5  6  7  8  9 - r, node.idx        | | d
x  1  2  1  4  5  5  4  1 - d, parent.idx      | |
                                               | | backward-oriented
                                               | | -----------------
default post-order (POST)                      | | forward-oriented
-----------------------------------------      | |
b  d  f  g  e  c  i  h  a - n, trace         <-| |
1  2  3  4  5  6  7  8  9 - r, node.idx          |
9  6  5  5  6  9  8  9  x - d, parent.idx        |
                                                 |
reversed post-order (POSTR)                      |
-----------------------------------------        |
i  h  g  f  e  d  c  b  a - n, trace           <-|
1  2  3  4  5  6  7  8  9 - r, node.idx
2  9  5  5  7  7  9  9  x - d, parent.idx
```

<!-- ======================================================================= -->
## overall remarks

Note that each parent reference can be described as the instance of an abstract
property that was used to **mark** (or color, highlight) all those nodes that
belong to the same child order. This is most visible in the sequence of parent
references of the level-order tree traversal.

Note that the default pre-order (PRE) trace is equal to reversed sequence of
the reversed post-order (POSTR) trace. Similar to that, the default post order
(POST) trace is equal to the reversed sequence of the reversed pre-order (PRER)
trace.

* `PRE(a,b,c,d,e,f,g,h,i) <=> POSTR(i,h,g,f,e,d,c,b,a)`
* `POST(b,d,f,g,e,c,i,h,a) <=> PRER(a,h,i,c,e,g,f,d,b)`

Note that the **PRE-POSTR** and the **POST-PRER** correspondence does not
directly apply to the sequences of parent references. That is because these
references depend on the corresponding index orders, which do not match since
the corresponding traces of nodes are not identical.

* `PRE(x,1,1,3,3,5,5,1,8) <=!=> POSTR(2,9,5,5,7,7,9,9,x)`
* `POST(9,6,5,5,6,9,8,9,x) <=!=> PRER(x,1,2,1,4,5,5,4,1)`

Note however that the parent references can be transformed `(#d+1-d[i])` based
on the sequence lengths. This allows to state that even these sequences still
correspond with each other.

* `PRE(x,1,1,3,3,5,5,1,8) <=> POSTR*(8,1,5,5,3,3,1,1,x)`
* `POST(9,6,5,5,6,9,8,9,x) <=> PRER*(x,9,8,9,6,5,5,6,9)`

Note that only the LVL, PRE, and PRER traversals are **backward-oriented**.
That is, the values of the parent reference are all lower than the value
of the corresponding node references. In contrary to that, the POST and
PROSTR traversals can be described as **forward-oriented**.

* `(d[i] < r[i])` for all `(i in [1,#r])` and `LVL,PRE,PRER`
* `(d[i] > r[i])` for all `(i in [1,#r])` and `POST,POSTR`

Note that **cycles** can be detected by comparing the values of the parent
references with the value of the reference of the corresponding node. That is
because one or more parent reference must the be actainst the afore mentioned
default orientation.

Note that only the LVL, PRE and PRER traces are such that the document tree's
**root is first**. That is because these tree traversals are order-preserving
in regards to the node order of the unordered document tree (DTU). In contrary
to that, the doctree's **root is last** with POST and POSTR. That is because
these traversals visit a node after all of their descendants in DTU have been
visited. Because of that, these traversals are not order-preserving in regards
to DTU.
