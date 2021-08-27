
<!-- ======================================================================= -->
# downward and/or upward total orders

orientation of downwards/upwards
* (a < b), (down -> up) := "a" is down, "b" is up
* arrows always point upwards to subsequent items

<!-- ======================================================================= -->
## downward total poset (non-standard)

* if (a < c) and (b < c), then also (a related-to b)

remarks
* total against the edges, towards a root
* each node has one root node only
* disallows "parallel subcomponents"

remarks
* the standard definition uses (<=) instead of (<)

<!-- ======================================================================= -->
## upward total poset (non-standard)

* if (a < b) and (a < c), then also (b related-to c)

remarks
* total with the edges, towards a leaf
* each node has one leaf node only
* disallows "parallel subcomponents"
* seems to have no standard definition

<!-- ======================================================================= -->
## total order

* a trichotomous/connext poset
* i.e. all pairs must be connected

Note that a total order is both "downward- and upward-total". However, the
description as "downward- and upward-total" is not sufficient to force all pairs
to be connected. That is because they allow a forest of disjoint path graphs.

<!-- ======================================================================= -->
## prefix-/suffix-order - (don't use !)

A downward-total poset may be described as **a prefix order**.
Likewise, a upward-total poset may be described as **a suffix order**.

Note that the description as "prefix/suffix order" is **misleading**, since
these are structural definitions (i.e. downward-/upward-total) and as such
independent from the elements the order contains. Because of that, the use
of these terms should be avoided. That is, one should stick with descriptions
such as "a downward-/upward-total poset" instead.

Note that "prefix" in "prefix order" needs to be seen in regards to the rooted
path over the tree. Likewise, "suffix" in "suffix order" needs to be seen in
regards to the path that begins in a node and ends in the single leaf.

Note that an induced subtree can be seen as a suffix to a tree. Likewise,
a rooted path can be seen as a (special) prefix. However, these extended
definitions of prefix/suffix have nothing to do with the prefix/suffix order.
