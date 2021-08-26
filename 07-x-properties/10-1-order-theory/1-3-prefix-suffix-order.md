
<!-- ======================================================================= -->
## prefix order (standard)

An order relation such that the following condition is met
can be described as being **downward-total**:

* if (a <= c) and (b <= c), then also (a <= b) or (b <= a)

A partial order that is also downward-total can be described as
**a prefix order**. Based on that, a prefix-order can be understood
to generalize the concept of a tree by requiring a certain characteristic.

<!-- ======================================================================= -->
## downward/upward total (non-standard)

An order relation such that the following condition is met
can be described as being **downward-total**:

* if (a < c) and (b < c), then (a related-to b)

An order relation such that the following condition is met
can be described as being **upward-total**:

* if (a < b) and (a < c), then (b related-to c)

Note that the overall focus of this discussion is on non-reflexive (aka. strict)
and directional order relations. Also, each element is considered unique.

<!-- ======================================================================= -->
## prefix/suffix order (non-standard)

A poset that is downward-total can be described as **a prefix order**.
A poset that is upward-total can be described as **a suffix order**

<!-- ======================================================================= -->
## remarks

* (a < b), (down -> up) := "a" is down, "b" is up

Note that, even though the description as "a prefix/suffix order" is based upon
the prefixes/suffixes of strings/sequences, the elements in that order are in
principle not required to be actual sequences/strings.

Note that the rooted path of a node can be seen as a prefix of the corresponding
tree. However, that point of view does not cover the definition based on the
removal of one suffix only. That is, one will in general have to remove several
suffixes (i.e. induced subtrees) from a tree in order to end up with the rooted
path of a node.
