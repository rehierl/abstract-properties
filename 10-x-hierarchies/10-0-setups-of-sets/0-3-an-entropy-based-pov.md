
<!-- ======================================================================= -->
# an entropy-based point of view on relationships

Note that the overall focus of the following discussion is on how information
can in general be embedded into a setup of sets. That is, the information
encoded into a setup will not be provided by directly the elements in the
set-based items, but by the relationships between the sets themselves.

Any class/family/setup/set of sets (S) can be thought of as being formed from
a universal set of elements (U) such that each set in (S) is a subset to (U).
Because of that, each setup is a subset to the powerset over its universal
set of elements.

Since an arbitrary subset (S) to the powerset of (U) has no characteristics
which could be relied upon, the first step is to define requirements that a
setup needs to satisfy.

* arbitrary subsets have no characteristics that could be relied upon

One such requirement is that, due to the characteristics of the empty set, no
set in (S) can be allowed to be empty. That is, a setup must be required to be
a set of non-empty sets.

* a setup must not contain the empty set

As such, a setup of sets may correspond with a set of sets such that the sets
in it are pairwise disjoint. That is, no element in (U) is an element of two
or more sets in (S). Hence, each element belongs to one and only one set in
(S). In such a case, (S) is a partition of (U) and (U) the union of pairwise
disjoint sets.

Even though there are many ways to form a set of pairwise disjoint sets from a
universal set, the relationships between all pairs of distinct sets in such a
setup will always be the same - i.e. "disjoint". And since there is no entropy
in the relationships between such sets, these kind of setups do not allow to
encode any additional information. From that point of view, a setup must have
one or more sets that have one or more elements in common.

* not all the sets in a setup can be disjoint

The other extreme case would be to have a multiset of sets such that all the
sets in it are identical. Put differently, all the elements in (U) are elements
to all the sets in (P). As before, such a setup could be described to have no
entropy in the relationships between its sets (i.e. all the sets are "equal")
and would thus not allow to encode any additional information. With that in
mind, a setup must have one or more sets that differ in one or more elements.

* a setup should consist of more than one set

That is, in order to make use of the relationships between sets, a setup
needs to have distinct non-empty sets and needs to support different types
of relationships between its sets. Hence, the focus of this chapter needs
to be on the relationships between sets of elements.
