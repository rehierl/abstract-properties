
<!-- ======================================================================= -->
# example - remove a suffix from a tree

```
S                 \ R            = S*
========================================
( 1 -> 2 -|-> 3 ) \ ( 2 -|-> 3 ) = ( 1 )
          |-> 4          |-> 4
```

In general, given a tree `S` and a to-be-removed node (e.g. `2`), we implicitly
treat the node and its descendants as a composite unit. That is, the scope of
an operation has in general the tree order as its base order. Such an operation
may therefore be described as **a suffix-based removal**.

Note that the element-based removal is from a generalized point of view also
a suffix-based removal. That is, a suffix over the trivial base order is
removed from the input order. It just so happens that each suffix of that base
order always only consists of a single element.

Since a tree can be understood as the cover graph of a partial order, this type
of removal can also be understood from **an order-based perspective**. That is,
the resulting suborder `S*(U,<)` can be said to be formed by removing an induced
suborder `R(T,<)` from an input order `S(V,<)`.

* `S* := (S \ R)` where `R := S[2,*]`

Note that only the input node, its descendants and the edges between them are
removed explicitly. That is because these elements are elements in the induced
subtree. In contrary to that, all the (border) edges in the order relation of
`S`, which connect a node in the resulting tree `S*` with a node in the induced
sub-tree `R` (i.e. `(1,2)`, `(1,3)` and `(1,4)` - in regards to the underlying
node order) must be removed implicitly. That is because, a node can not remain
related to a node that was removed.
