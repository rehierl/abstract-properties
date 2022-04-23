
<!-- ======================================================================= -->
# a suffix/prefix-based point of view

Recall that each ordered sequence, including the pre-order trace of a tree,
corresponds with a path graph - i.e. a specialized node tree. Because of
that, **each non-empty suffix** over an ordered sequence can be understood
to correspond with **an induced subtree**, which is why one can describe
`TU[n]` and `TO[n]` as suffixes over the corresponding node orders.

* `suffix := T[n] := [n,*]`

Conversely, the **prefix** of an ordered sequence can be described as what
remains if a suffix is removed from an ordered sequence.

* `prefix := order(x) \ suffix(y)`

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

Note that, since `TU[n]` is obviously strictly speaking no subtree of `TO[n]`,
one needs to **focus on the resulting subset of nodes** that can be used to
form an induced suborder/subgraph over the corresponding node order.

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
node is what remains if `TO[fc]` and `TO[ns]` are both removed from `TO[n]`.
Because of that, and in contrary to a linear order, a tree order is in general
such that it has **multiple disjoint suffixes**, each of which can be removed
independently.

* `prefix := order(x) \ suffix(y) \ suffix(z)`

Note that, in the context of a linear order, suffix `y` will contain suffix
`z` (or vice versa), which is why one of these subterms will have no effect.
In contrary to that, it is not possible to drop one of the terms in the
context of a tree order, if both suffixes are disjoint - i.e. both suffixes
are located on different branches.
