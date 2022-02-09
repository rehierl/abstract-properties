
<!-- ======================================================================= -->
# general remarks on setups of rpaths

<!-- ======================================================================= -->
## howto distinguish cases

Assumed that `S` is a valid partial setup of rooted paths, then ..

In order to determine if two paths `(s,t in S)` in `S` are **disjoint**,
one only needs to test if both have the same first node.

* `(s disjoint-to t) <-> (s[1] != t[1])`

In order to determine if two coupled paths in `S` are **related** with each
other, one only needs to determine if the last node of the shorter path is
a node in the other path.

* `(s related-to t) <-> (s[1] == t[1]) and (s[i] == t[i])`
* for `i := min(#s,#t)`

If that is not the case, then both paths **overlap** each other.

* `(s overlaps t) <-> (s[1] == t[1]) and (s[i] != t[i])`

Note that, if two paths in `S` are related, then one can determine the
ancestor and the descendant by simply comparing the lengths of both paths.
That is because the shorter path must be an ancestor to the other path.

* `(s ancestor-of t) <-> (s related-to t) and (#s < #t)`

<!-- ======================================================================= -->
## DI-RE-OV, union of setups

When forming a union of two setups, one can in general not guarantee that the
universal sets of both setups are disjoint. That is, two distinct setups may
contain paths that share any number of nodes in any order. (Note - the union
of two paths, each of which belongs to a different setup, may form an "X" -
i.e. contains a node that has two parents and two child nodes).

Note that, even though general operations on setups of rooted paths are not
the focus of this discussion, the union of non-disjoint setups could be used
in order to add one or more nodes to a tree. However, care must be taken in
order for the resulting union to not break the requirements of such a setup.
