
<!-- ======================================================================= -->
## trees in (descriptive) set theory (DST)

One kind of well-behaved sets in DST is analogous to the concept of node trees
in Graph Theory:

A tree in DST is a collection of sequences `S` over a set of elements `N` such
that every prefix `p` of every sequence in `S` is also a sequence in `S`.

* for `(S subset-of ×N)`
* if `(t prefix-of s)` for `(s in S)`, then also `(t in S)`

Note that one might already suspected that the set of all rooted paths `RP`
over a node tree is yet another method that allows to describe a node tree.
