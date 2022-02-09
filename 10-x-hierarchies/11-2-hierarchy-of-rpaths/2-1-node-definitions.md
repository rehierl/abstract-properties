
<!-- ======================================================================= -->
# remarks about the embedding of node definitions

Recall that it is essential for the isomorphism between a node tree and a
hierarchy of elements that each element has one and only one characteristic
element embedded into it. This CE must be used as a node reference which
denotes the node that the corresponding element represents in the node tree.

<!-- ======================================================================= -->
## characteristic subsets (CSS) and elements (CE)

Since the related-to operator of a partial setup of rooted paths is based on
the prefix-of operator, all the nodes of the ancestors of a path are nodes in
the path of a descendant. That is, unlike a hierarchy of induced subtrees (Ht),
the inner subset of a path `iss(s)` consists of all the nodes in its parent
`p(s)`, which is a prefix to path `s`. The characteristic subset (CSS) of a
path therefore corresponds with a non-empty suffix to that path.

* `s := (iss(s) × css(s))` where `(iss(s) == p(s))`

Since a partial setup has no requirement that restricts the length of a suffix
to one characteristic element (CE) only, any path may have any number of such
elements. Because of that, and without further requirements, a general partial
setup of rooted paths can not yet be understood to hold the strict definition
of a tree.

Note that, unlike with scopes, no `css(s)` in a setup of rooted paths can be
empty. That is because a child `c` must hold at least one node in addition to
its parent `p`. As a matter of consequence, no non-root parent can exist that
has an empty characteristic subset since any such parent is a child to its
very own parent.

* `(#css(s) > 0)` is true for any `(s in S)`

Due to the above, and in order to ensure that each path has one and only one
CE, a forest/hierarchy of rooted paths must be required to include every prefix
of each path it holds.

* if a forest `F` includes all the prefixes of each path `(s in F)`, then ..
* `(#css(s) == 1)` is true for any `(s in F)`

<!-- ======================================================================= -->
## index-based setups

Provided that one has an ordered sequence of node definitions `n`, one can
still define an ordered sequence of rooted paths `S` such that the index of
each path can be used to lookup the corresponding node in `n`. In addition
to that, the CE of each rooted path can be replaced by the path's index.

* `n := (n1..nN)`, `S := (s1..sN)`
* and `(n[i] == S[i])` for `(i in [1,#S])`
* and `(ce(si) == i)`, and `(s[#s] == i)`

Note that an index-based setup of rooted paths can be used to transition from
a sequence of rooted paths **towards a sequence of node levels**, and also
from a sequence of rooted paths **towards a sequence of length values**. Both
encodings can be understood to count the corresponding elements and, based on
that, to encode the structure of a tree.
