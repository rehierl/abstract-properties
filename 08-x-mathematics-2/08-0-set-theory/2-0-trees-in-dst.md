
<!-- ======================================================================= -->
# trees in (descriptive) set theory (DST)

One kind of "well-behaved" sets in DST is
analogous to the concept of node trees in Graph Theory:

A tree `T` in DST is a collection of sequences `S` over a set of elements `N`
such that every prefix `p` of each sequence in `T` is also a sequence in `T`.

* for `(S subset-of ×N)`
* if `(t prefix-of s)` for `(s in T)`, then also `(t in T)`

In words: A tree in DST is a prefix-ordered set of sequences `T` over a set of
elements `N` such that every prefix of a sequence is also a sequence in `T`.

Recall that `×N` denotes the concatenation-based product (sequences) over the
elements in `N` of possibly infinite length. Also, the overall context of this
discussion is on finite sets of elements and on sequences of finite length.
Because of that, `×N` must be read as "all possible sequences over set N of
finite length".

Note that one might already suspected that the set of all rooted paths `RP`
over a node tree is yet another method that can be used to describe node trees.

<!-- ======================================================================= -->
## analogous definitions

There are specific definitions for this particular set-based context which have
a graph-based counterpart. These set-based definitions are however non-relevant
to this discussion. The following will therefore only mention a few in order to
give a general impression.

A **branch** is an infinite sequence over `N` such that each prefix it contains
is also a prefix in `T`.

Note that the context of this discussion is on finite sets/sequences.
Despite that, a branch does carry the notion of an "infinite" rooted path.

A tee that has no such branch can be described as **well-founded**. Otherwise,
the tree can be described as **ill-founded** (i.e. one or more branches).

Note that, in this context, the set of elements is the set of all prefixes of
a given sequence. Combined with the prefix-of operator, the prefix `s` of a
prefix `t` can be considered "smaller than" `t`. Based on that, point of view
a branch can be described as a well-founded total order relation.

A **terminal node** is a finite sequence that is no prefix to another sequence.
Furthermore, a tree that has no such terminal node can be described as
**a pruned tree**.

Note that a "terminal node" does carry the notion of "root node". With that in
mind it might seem odd that there could be trees with no root. However, if one
recalls that the focus of DST is on sets of real numbers, then one can also
recall that the real line is infinite in both directions and has as such "no
root/least" element.
