
<!-- ======================================================================= -->
## prefix order

An order relation such that the following condition is met
can be described as being **downward-total**:

* if `(a <= b)` and `(b <= c)`, then also `(a <= b)` or `(b <= a)`

A partial order that is also downward-total can be described as
**a prefix order**. Based on that, a prefix-order can be understood
to generalize the concept of a tree by requiring a certain characteristic.

Note that, even though the description as "a prefix order" is based upon the
prefixes of a string, the elements in that order are in principle not required
to be actual sequences/strings.

Note that the rooted path of a node can be seen as a prefix of the corresponding
tree. However, that point of view does not cover the definition based on the
removal of one suffix only. That is, one will in general have to remove several
suffixes (i.e. induced subtrees) from a tree in order to end up with the rooted
path of a node.
