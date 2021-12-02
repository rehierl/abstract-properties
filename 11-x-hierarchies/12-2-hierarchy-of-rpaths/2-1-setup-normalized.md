
<!-- ======================================================================= -->
# normalized setup

A simple setup `S` can be described as **a normalized setup**,
if the following requirements are met:

* (R0) `S` is a simple setup of rooted paths.
* (R1) Each CE can be treated a unique node reference.

Note that no explicit requirement is needed to ensure that the characteristic
subset of each path in a partial setup of rooted paths has one and only one
characteristic element. That is because such a setup is required to contain
a path and all of its prefixes, which implicitly guarantees that each CSS
is a 1-element subset.

* `(#css(s) == 1)` is true for all `(s in S)`
* `U(S)` is effectively a set of node references

<!-- ======================================================================= -->
## index-based setup

As explained before, each index-based setup of sets is effectively the encoding
of a normalized setup. In contrary to that, a setup of rooted paths is such
that the CSS of no path can be empty or contain more than one element. In
addition to that, the CSS of no path can be reduced to an empty set, since all
the prefixes of a path are related with each other (unlike the disjoint child
sets of a parent set in a setup of scopes). That is, any setup of rooted paths
is minimal in regards to its characteristic subsets.

Despite that, and provided one has an ordered sequence of nodes `n`, one can
still define an ordered sequence of rooted paths `S` such that the index of
each path can be used to lookup the corresponding node in `n`. In addition
to that, the CE of each path can be replaced by the corresponding index.

* `n := (n1..nN)`, `S := (s1..sN)`
* and `(n[i] == S[i])` for `(i in [1,#S])`
* and `(ce(si) == i)`, and `(s[#s] == i)`

Note that an index-based setup of rooted paths can be used to transition from
a sequence of rooted paths towards a sequence of node levels, and also from a
sequence of rooted paths towards a sequence of length values. Both encodings
can be understood to count the corresponding elements and, based on that, to
encode the structure of a tree.
