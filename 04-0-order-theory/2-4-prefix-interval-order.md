
Note that the following content is kept as a reminder of "confusing" (i.e.
non-intutitive) naming conventions.

<!-- ======================================================================= -->
## prefix order

An order relation such that the following condition is met
can be described as being **downward-total**:

* if `(a <= b)` and `(b <= c)`, then also `(a <= b)` or `(b <= a)`

A partial order that is also downward-total can be described as
**a prefix order**. Based on that a prefix-order can be understood
to generalize the concept of a tree by requiring a certain characteristic.

Note that, even though the description as "a prefix order" is based upon the
prefixes of a string, the elements in that order are in principle not required
to be actual sequences/strings.

Note that the rooted path of a tree can be seen as some sort of prefix. However,
and in the context of a tree, that point of view does not cover the definition
based on the removal of one suffix only. That is, one will in general have to
remove several suffixes (i.e. induced subtrees) from a tree in order to end up
with the rooted path of a node.

<!-- ======================================================================= -->
## interval order

An interval order `P := (I,<)` consists of a set of intervals `I` on real
numbers and an order over these intervals that is defined as follows:

* `i := [iLe,iRi]` for `(i in I)`
* `(i < j) := (iRi < jLe)` for `(i,j in I)`
* note - `i` is completely left of `j`

An order may be described as an interval order, if it is order-isomorphic to
such an interval order.
