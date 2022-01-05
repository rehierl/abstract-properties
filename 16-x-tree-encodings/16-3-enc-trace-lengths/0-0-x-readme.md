
<!-- ======================================================================= -->
# A pre-order length-based encoding

Recall that any ordered tree `T` is isomorphic to its hierarchy of pre-order
traces `Hpre`.

* The first node of each trace, its CE, denotes the node a trace represents.
* The parent of a trace is its least significant (i.e. shortest) superstring.
* The offset of each child trace in its parent trace defines the child order.

<!-- ======================================================================= -->
## a bottom-up based approach

```
ordered tree =>                => tree of traces
================================================
 A        |  A         |  A         |  ABCDEF
--------- | ---------- | ---------- | ----------
 B     F  |  B      F  |  BCDE   F  |  BCDE   F
------    | -------    | -------    | -------
 C  D     |  C  DE     |  C  DE     |  C  DE
   ---    |    ---     |    ---     |    ---
    E     |     E      |     E      |     E
```

Instead of beginning with the root of a document tree `T`, one can begin with
its leaf nodes and iteratively "push" the pre-order traces of all descendants
up towards the root.

* `S0 := { }`
* `S1 := { C, E, F }`
* `S2 := { C, E, F, DE }`
* `S3 := { C, E, F, DE, BCDE }`
* `S4 := { C, E, F, DE, BCDE, ABCDEF }`

As one can see, the pre-order trace of a node is a **substring** to the trace
of its ancestors, and possibly even a suffix to these superstrings. Because of
that, each trace has a least and a most significant superstring (i.e. in terms
of the length of each trace). Based on that, all pre-order traces combined can
be understood to form a **hierarchy of pre-order traces** `Hpre`.

* `Hpre(T) := S4 := { ABCDEF, BCDE, C, DE, E, F }`

Note that this approach can be described to be **in reverse** to a level-order
traversal. That is because it begins with the leaf nodes at the lowest level,
continues with the nodes at the next upper level, and ends with the doctree's
root. Because of that, this approach could be implemented by iterating over
the doctree's level-order trace in reverse - i.e. beginning with its last node
and finishing with its first/root node.

Note that the difference to a top-down approach is that this approach prodcues
**complete pre-order traces**. That is, once created, the sequences associated
with a node will not be modified by any subsequent step.

<!-- ======================================================================= -->
## a length-based encoding

Since each pre-order trace is an ordered sequence of nodes, and since the trace
of each node `pre(n)` is a substring to the traces of its ancestors, each trace
can be understood to have unique offsets in the traces of its ancestors and thus
also in the trace of the document tree's root `pre(r)`. One can therefore form
a sequence of length values `len(T)` by replacing each node in the document
tree's trace `pre(T)` by the length of the node's trace - i.e. `#pre(n)`.

* `len(T) := ( #pre(n) | (n := t[i]) for (i in [1,#t]) and (t := pre(T)) )`

```
 trace    | pre-order traces        | Hpre   | # | length-based encoding
============================================================================
 A        | n: ( A  B  C  D  E  F ) | ABCDEF | 6 | n:   ( A, B, C, D, E, F )
--------- | r: ( 1  2  3  4  5  6 ) | BCDE   | 4 | r:   ( 1, 2, 3, 4, 5, 6 )
 B     F  |     -A---------------   | C      | 1 | len: ( 6, 4, 1, 2, 1, 1 )
------    |        -B--------- -F   | DE     | 2 |
 C  D     |           -C -D---      | E      | 1 |
   ---    |                 -E      | F      | 1 |
    E     |                         |        |   |
```

Note that a length value `len[i]` in combination with its offset/index `i` form
an interval that denotes the first and the last node of the corresponding trace.
That is, the trace `pre(x)` of a node `x` can be derived from a document tree's
pre-order trace `n(T)` and the length value associated with that node.

* `pre(x) := n[i,j]` for `(n[i] == x)` and `j := (i+len[i]-1)`

Since all traces are substrings to the root's trace, one can form the hierarchy
of traces `Hpre` of a document tree from its pre-order trace `pre(T)` and its
sequence of length values `len(T)`.

* `Hpre(T) := { pre(x) | (x in n(T)) }`

Note that the **structure definition** of the document tree is completely
embedded into its sequence of length values.

<!-- ======================================================================= -->
## characteristics of len(T)

Since `n(T)` always begins with the document tree's root, and always ends in
a leaf, `len(T)` begins with the total number of nodes `#N`, and ends in a
value of `1`. Despite that, no other general statement can be made about any
other value in `len(T)`.

* `n[i]` is the root node, if `(len[i] == #len)`
* all nodes in `n[a,b]` are descendants of `n[i]`
  if `a := (i+1)` and `b := (i+len[i]-1)`
* `n[i]` is a parent, if `(len[i] > 1)`
* `n[i]` is a leaf, if `(len[i] == 1)`
* `len(T) := (#N,..,1)` for `(#N == #len(T))`

Note that these characteristics obviously require that a sequence of length
values is used to encode a single tree. That is, certain aspects change, if
a sequence of length values is used to encode a forest.

<!-- ======================================================================= -->
## edge cases of len(T)

```
    A      |  len(T) := ( #N,1,..,1 )
---------  |  lvl(T) := ( 1,2,...,2 )
 B C D E   |  pre(A) := ( A,B,C,D,E )
```

If a general tree is such that only the root has child nodes, then only the
first value is greater than one. To be more accurate, the first length value
is the number of nodes in the document tree's set of nodes `N`.

```
 A   |  len(P) := ( #N,#N-1,..,2,1 )
---  |  lvl(P) := ( 1,2,..,#N-1,#N )
 B   |  pre(A) := ( A,B,C )
---  |  pre(B) := (   B,C )
 C   |  pre(C) := (     C )
```

If a general tree is a path graph `P`, then the doctree's sequence of length
values `len(P)` is strictly monotone decreasing. In contrary to that, the
tree's sequence of level values `lvl(P)` is strictly monotone increasing and
because of that reverse to `len(P)`.

* `(len[i]-1 == len[i+1])` is true
* `(len(P) reverse-to lvl(P))` is true
