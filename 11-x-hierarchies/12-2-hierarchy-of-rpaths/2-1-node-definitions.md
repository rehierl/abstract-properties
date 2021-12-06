
<!-- ======================================================================= -->
# remarks about the embedding of node definitions

Recall that it is essential for the isomorphism between a node tree and a
hierarchy of elements that each element has one and only one characteristic
element embedded into it. This CE must be used as a node reference which
denotes the node that the corresponding element represents in the node tree.

<!-- ======================================================================= -->
## characteristic subsets and elements

Recall that a partial setup is defined such that it contains any prefix of any
rooted path it contains. Because of that, the characteristic subset **CSS** of
a rooted paths is formed by removing all the nodes in each ancestor path. Each
rooted path is therefore guaranteed to have one and only one characteristic
element **CE**.

* `(#css(s) == 1)` is true for any `(s in S)`

Note that, since any rooted path in a partial setup of rooted paths has one CE
only, any such setup can be described as a normalized setup of rooted paths.
Based on that, each rooted path can be understood to have **its last node**
as its one and only CE.

* `ce(s) := s[#s]`

Note that the set of all characteristic elements `CE(S)` in a partial setup of
rooted paths is equal to its universal set of all elements `U(S)`, which must
be understood as a set of node references.

* `(CE(S) == U(S))` is true

Note that the CSS of no rooted path in such a setup can be empty.

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
