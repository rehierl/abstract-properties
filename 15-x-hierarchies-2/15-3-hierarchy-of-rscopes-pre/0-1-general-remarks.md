
<!-- ======================================================================= -->
# general remarks

<!-- ======================================================================= -->
## relevant previous isomorphisms

**T-Hrp** - A tree (T) allows to form a hierarchy of rooted paths (Hrp) such
that the source tree can be recreated based on the relationships between its
paths. However, such a hierarchy does not embed the child order of a document
tree (DT). That is because there is no order over the paths in Hrp.

**T-Hrs** - A tree (T) allows to form a hierarchy of reversed scopes (Hrs)
such that the source tree can be recreated based on the relationships between
its scopes. However, such a hierarchy does not embed the child order of a
document tree (DT).

**DT-Hpre** - In contrary to the above, a document tree (DT) allows to form a
hierarchy of pre-order traces (Hpre) such that the source tree, including its
child order, can be recreated based on the relationships between its traces.
That is because the child order is already embedded into the document tree's
trace (i.e. the trace of its root) and also (partially) into the traces of
every induced subtree over DTU.

<!-- ======================================================================= -->
## about the description of "reversed scopes" (2)

Recall that the description of "reversed scopes" is in regards to upward-closed
open intervals (i.e. `[*,n]`), in contrary to the definition of default scopes
as downward-closed open intervals (i.e. `[n,*]`). Because of that, the scopes
of each type can be described in terms of the ancestors/descendants of the
defining node.

* `Hrs(n) := A*(n)` and `Hs(n) := D*(n)`

Recall that the reversed scope of a node is a scope over the reversed graph,
which can be formed if the orientation of each edge in the source tree is
reversed (i.e. edge `(1,2)` becomes edge `(2,1)`).

Note that this applies to a path graph, as well as to an unordered document
tree (DTU). The question is, how this description exactly applies in the
context of an ordered document tree (DTO).

```
the node order of an ordered document tree (DTO)
=======================================================
r -> .. -> p -> fs -> .. -> ps -> n -|-> ns -> .. -> ls
                                     |-> fc -> .. -> lc

the reversed node order (G) - not a tree!
=======================================================
ls -> .. -> ns -|-> n -> ps -> .. -> fs -> p -> .. -> r
lc -> .. -> fc -|
```

Recall that visualizations orient the edges from "top to bottom" and "left
to right". That is, the ordered tree (DTO) has an edge `(ps,n)` whereas graph
(G) has an edge `(n,ps)`.

As can be seen above, the scope `s(n) := [n,*]` of node `n` over the node
order of the reversed document tree (G) still corresponds with the reversed
scope `rs(n) := [*,n]` over the ordered document tree (DTO). That is, the
sets of nodes in both intervals are equal.

* `A(n,T) <-> D(n,G)`

Note that, since the child order of the document tree is embedded into the
ordered document tree in reverse (i.e. `(lc..fc)` rather than `(fc..lc)`), one
should also flip the reversed graph of a planar document tree on the vertical
axis to indicate that the doctree's child order must also be reversed when an
unordered document is reversed.

```
a document tree DT         the reversed graph G
==================   <=>   ====================
       0                           6   5
       |                           |   |
 -------------                     -----
 |   |       |                       |
 1   2       7               9   8   4   3
     |       |               |   |   |   |
   -----   -----             -----   -----
   |   |   |   |               |       |
   3   4   8   9               7       2   1
       |                       |       |   |
     -----                     -------------
     |   |                           |
     5   6                           0
```

Due to the above, one can state that the description "reversed scope" is still
applicable (i.e. "makes some sense") in the context of a document tree.
