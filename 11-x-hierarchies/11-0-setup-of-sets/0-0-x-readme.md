
* overall too verbose
* should only provide a quick overview

<!-- ======================================================================= -->
## todo - seems ok-ish

* the aspect about entropy is good

Any class/family/set of sets (S), referred to as a setup of sets, can be
thought of as being formed from a universal set of elements (U) such that
each set in it is a subset to (U). Because of that, each setup is a subset
to the powerset over its universal set of elements.

Since an arbitrary setup of sets (S) has no characteristics which could be
relied upon, the very first step is to define additional requirements that
need to be satisfied. One such requirement is that, due to the characteristics
of the empty set (in regards to non-empty sets), no set in (S) is allowed to
be empty. That is, a setup is required to be a set of non-empty sets.

As such, a setup of sets may correspond with a set of sets such that the
sets in it are pairwise disjoint. That is, no element in (U) is an element
of two or more sets in (S). Hence, each element belongs to one and only one
set in (S). In such a case, (S) is a partition of (U) and (U) the union of
pairwise disjoint sets.

Even though there are multiple different ways to form a set of pairwise
disjoint sets from a universal set, the relationships between all pairs of
distinct sets in such a setup will be exactly the same - i.e. "disjoint".
And since there is no entropy in the relationships between such sets, these
kind of setups do not allow to encode any additional information. From that
point of view, a setup needs to have one or more sets that have one or more
elements in common.

The other extreme case would be to have a multiset of sets such that all the
sets in it are identical. Put differently, all the elements in (U) are elements
to all the sets in (P). As before, such a setup would have no entropy in the
relationships between its sets (i.e. all the sets are "equal") and would thus
not allow to encode any additional information. With that in mind, a setup
needs to have one or more sets that differ in one or more elements.

<!-- ======================================================================= -->
## todo - needs an overhaul

* the conclusion about the available types of relationships not so much
* i.e. edges are based upon a directional relationship - superset/subset
* i.e. not disjoint/equal/overlap

That is, and in order to make use of the relationships between sets, a setup
needs to have distinct non-empty sets and needs to support different types
of relationships between its sets. Because of that, the focus of this chapter
is on the relationships between sets of elements. As it turns out, only the
following three types can be unambiguously defined:

* (A disjoint-to B) := No element in A is an element in B.
* (A subset-of B) := All the elements in A are elements in B.
* (A equal-to B) := All the elements in A and B are elements in both.

In general two sets are said to be related with each other, if one is a
subset to the other. That is, in contrary to "subset-of", "related-to" has no
orientation. Put differently, and only knowing that two sets are related, one
can not tell which of the two is the subset and which the superset. In order
to make that distinction, one would have to compare the elements of both sets,
or respectively the amounts of those in each set.

* (A related-to B) := (A subset-of B) and/or (B subset-of A)
* (A equal-to B) := (A subset-of B) and (B subset-of A)
* i.e. equal sets are related to each other

One further distinct type of relationship (i.e. "overlaps") could still be
defined. However, this definition is less strict than the previous ones. That
is because it requires both sets to have one or more elements in common and
one or more elements that are unique to each set. Hence, both sets are neither
disjoint (i.e. coupled), nor is one set a subset of the other (i.e. unrelated).
A less formal description would therefore be that overlapping sets share some,
but not of all their elements. (Note the quality of the qualifiers involved:
"all", "none", "some"). Hence, the question is "How many elements do both
sets need to have in common?". Obviously, the answer to that can in general
only be relative (i.e. "some"), not absolute (i.e. "all" or "none").

* (A overlaps B) := (A coupled-with B) and (A unrelated-to B)
* (A coupled-with B) := (A not-disjoint-to B)
* (A unrelated-to B) := (A not-related-to B)

<!-- ======================================================================= -->
## todo - needs an overhaul

Because of that, there are only two strict types of relationships relevant
in the context of a setup (i.e. "disjoint" and "related"). Obviously, two
sets that are disjoint, can not be related with each other since they have
no element in common. Likewise, two sets that are related with each other,
can not be disjoint since both must have one or more elements in common.

Therefore, and in order to encode any additional information into a setup,
each pair of sets in a setup needs to be either a pair of disjoint ex-or a
pair of related sets. Put differently, if two sets in a setup have one or
more elements in common, then both sets must be (by requirement) related
with each other. As such, the "overlaps" relationship is excluded.

A setup can therefore be understood to represent a strict binary system of
two distinct types of relationships (i.e. disjoint (0) ex-or related (1)).
Because of that, a setup corresponds with a graph whose vertices represents
the sets in a given setup such that two of its vertices are connected by an
(undirected) edge, if the sets of both vertices represent are related with
each other. In other words, two sets of a setup are disjoint, if there is
no edge in the graph between the corresponding vertices.

A proper setup can therefore have two extreme cases: (1) all the sets are
disjoint, and (2) all the sets are strictly related. In case-2, all the sets
in such a setup are distinct and pairwise related. Even though case-2 is also
based upon a single type of relationship (i.e. "related-to"), there is an
important difference: "disjoint-to" and "related-to" have no orientation,
"subset-of" however does (i.e. is oriented). That is, in the context of two
distinct related sets one can still determine which is the super-set and
which the sub-set. One can therefore determine which of the two is less/more
significant than, or super/sub-ordinate to the other. In contrary to that,
and in the context of disjoint sets, one can not determine which is more
relevant than the other.

* for two distinct sets - i.e. (A != B)
* (A disjoint-to B) <-> (B disjoint-to A)
* (A related-to B) <-> (B related-to A)
* (A related-to B) <-> (A subset-of B) ex-or (B subset-of A)

This chapter therefore focuses on the characteristics of setups such that
its distinct sets are required to be (1) non-empty, and (2) related if they
have one or more elements in common. (Note that the 2nd requirement keeps
a setup from having overlapping sets).

Note that, if all the sets are pairwise related, then a setup corresponds
with a total order. If, in contrary to that, some are related and others
are disjoint, then a setup corresponds with a partial order.
