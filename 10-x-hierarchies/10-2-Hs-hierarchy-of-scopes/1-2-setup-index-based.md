
<!-- ======================================================================= -->
# index-based setups

Even though an ordered sequence of elements can be understood to define an
index-based order over the elements in it, the main aspect of using of an
**ordered sequence** to define a setup of sets is at this point not for its
index-order to apply to the sets, but to provide **index-based ids** for
the sets in it. That is, the sets may still hold elements of any kind.

These ids can then be used to lookup the corresponding node in an ordered
sequence of node definitions that needs to be provided separately, alongside
the ordered sequence of sets.

When choosing to provide numeric index-based ids via the index-order of an
ordered sequence of sets, one would certainly want to first **reduce** the
amount of elements in each set as far as possible. The following will point
out those aspects one should keep in mind.

Note that, as can be seen below, such an index-based setup can be understood
to encode a normalized setup. Despite that, it is doubtful if such an explicit
set-based encoding has any benefits over other encodings.

<!-- ======================================================================= -->
## no more than one CE per CSS

In case there is a set `s` that has a CSS with more than one CE, one can reduce
the CSS of `s` by removing any additional CE from each set in `A*(s)`, and add
it to the corresponding node definition instead.

<!-- ======================================================================= -->
## index-based CEs

Even though not a necessity, one should use the index-based id of each set as
the CE of such a set.

In case set `s` has a non-index CE, one should remove such a CE from each set
in `A*(s)` and then add `id(s)` to these sets instead, effectively replacing
the non-index CE by an index-based CE.

Note that this process effectively combines an implicit with an explicit
embedding of node identifiers.

<!-- ======================================================================= -->
## empty root sets, non-parent

A root that has no child may have an empty CSS. That is because there is no
relationship with another set that will have to be determined. Hence, such a
root can be reduced to the empty set.

Note that, even though the sequence-based setup could thus end up having more
than one empty set, one needs to keep in mind, that each empty set is still
associated with the corresponding index. Because of that, any empty set in a
sequence-based setup must be understood as the unique instance of a non-empty
set.

<!-- ======================================================================= -->
## non-empty leaf sets, non-root

Each non-root leaf set must be required to have a non-empty CSS. That is because
it would otherwise not be possible to determine the parent set of such a leaf.

<!-- ======================================================================= -->
## parent sets with a CE

Since a parent may have one and only one child, not every parent can be allowed
to have an empty CSS. That is because such a parent set would then be equal to
its child set. Because of that, one could not tell which instance is supposed
to be the parent and which the child set.

<!-- ======================================================================= -->
## parent sets with no CE

Since a parent set that has more than one child must contain all the CEs of
each descendant in its inner set, the inner set of such a parent is itself a
unique subset. Because of that, any CE of such a parent can be removed.

<!-- ======================================================================= -->
## decoding

If the CSS of each set that can be empty is required to be empty, and if the
CSS of each set that must be non-empty is required to only hold the index-based
id of the corresponding set, then such an index-based setup can be decoded into
a normalized setup such that each set has its index-based id as its one and
only CE.

(0) Read the ordered sequence of (minimized) sets `s := (s1..sN)`.
Note that the CSS of each set must at this point have no more than one CE.

(1) Determine the ancestors `A*(s)` of each set.
That is, one must determine the relationship of each set with every other set.

(2) For each set that has an empty CSS, add `id(s)` to each set in `A*(s)`.
Note that this applies to empty roots and parents with more than one child.

Note that step-2 can be used to verify the setup. That is, if one determines
that the CSS of a set is non-empty and contains more than one CE, or if the
single CE does not match the set's index-based id, the setup may be rejected
as being malformed.
