
<!-- ======================================================================= -->
# a suffix/prefix-based point of view

Recall that each ordered sequence, including the pre-order trace of a tree,
corresponds with a path graph - i.e. a specialized node tree. Because of
that, **each non-empty suffix** over an ordered sequence can be understood
to correspond with **an induced subtree**, which is why one can describe
`TU[n]` and `TO[n]` as suffixes over the corresponding node orders.

* `suffix := T[n] := [n,*]`

Conversely, the **prefix** of an ordered sequence can be described as what
remains, if a suffix is removed from an ordered sequence.

* `prefix := order \ suffix`

<!-- ======================================================================= -->
## a visual example

```
 |-TO[n]---------------|
 ||-------------TU[n]-||
 || n =|=> (fc .. lc) ||
 ||----|--------------||
 |     |=> (ns .. ls)  |
 |---------------------|
```

Based on the above, and with a less strict point of view in mind, one can
describe `TU[n]` as a prefix of `TO[n]` since `TU[n]` can be formed by
removing `TO[ns]` from `TO[n]`.

* `( TO[n] \ TO[ns] ) => TU[n]`
* `( TU[n] prefix-of TO[n] )` can be understood to be true

Note that, since `TU[n]` is strictly speaking no subtree of `TO[n]`, one
needs to **focus on the corresponding subset of nodes** that can be used
to form an induced subtree/suborder over the appropriate node order.

<!-- ======================================================================= -->
## disjoint suffixes

```
 |-TO[n]----------------|
 |        |-TO[fc]-----||
 | n =|=> | (fc .. lc) ||
 |    |   |------------||
 |    |                 |
 |    |   |-TO[ns]-----||
 |    |=> | (ns .. ls) ||
 |        |------------||
 |----------------------|
```

Note that even node `n` can be understood as a prefix of `TO[n]` since that
node is what remains, if `TO[fc]` and `TO[ns]` are both removed from `TO[n]`.
Because of that, and in contrary to a linear order, a tree order is in general
such that it has **multiple disjoint suffixes**, each of which can be removed
independently.

* `prefix := order \ suffix-1 \ suffix-2`

Note that, in the context of a linear order, `suffix-1` will in general
contain `suffix-2` (or vice versa), which is why one of these subterms will
have no effect. In contrary to that, it is not possible to drop one of the
terms in the context of a tree order since both suffixes may be located on
different branches.
