
<!-- ======================================================================= -->
# normalized setup

A partial/total setup `S` can be described as **a normalized setup**,
if the following requirement is met:

* (R1) Each CE must be a unique node identifier of some sort.

Note that each path in a partial setup of paths is guaranteed to have
a 1-element CSS and therefore a CE.

* `(#css(s) == 1)` is true for all `(s in S)`
* `U(S)` is effectively a set of node identifiers

<!-- ======================================================================= -->
## index-based setup

As stated before, each index-based setup of sets is effectively an encoding
of a normalized setup. In contrary to that, a setup of rooted paths is such
that the CSS of no path can be empty or contain more than one element. Because
of that, the CSS of each path can not be reduced even further. That is, any
setup of rooted paths is minimal in that regards.

Despite that, and provided one has an ordered sequence of nodes `N`, one can
still define an ordered sequence of rooted paths `S` such that the index of
each path can be used to lookup the corresponding node. In addition to that,
the CE of each path can also be replaced by the corresponding index.

* `N := (n1..nN)`, `S := (s1..sN)`
* for `s := S[i]` and `(i in [1,#S])`
* `(ce(s) = i)`, `(s[#s] = i)`
* also `(t[#s] = i)` for `(t in A*(s))`

NOTE - This can be used to transition from a sequence of rooted paths towards
a sequence of node levels. Also from a sequence of rooted paths towards a
sequence of length values. Both encodings can be understood to count the
corresponding elements and, based on that, to encode the structure of a tree.
