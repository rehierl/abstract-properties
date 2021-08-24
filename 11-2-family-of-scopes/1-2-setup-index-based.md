
<!-- ======================================================================= -->
# index-based setups

Even though an ordered sequence of elements can be understood to define an
index-based order over the elements in it, the use of an **ordered sequence**
to define a setup of sets is not for the index-based order to apply to the
sets themselves, but to define **index-based ids** for the sets in it. These
ids can then be used to lookup the corresponding node in an ordered sequence
of node definitions (i.e. an index-based mapping) that needs to be understood
to be provided separately, in addition to the ordered sequence of sets.

When choosing to provide numeric index-based ids via the index-order of an
ordered sequence of sets, one would certainly want to first reduce the amount
of elements in each set to an absolute minimum. The following will mention the
aspects one should keep in mind.

Note that an index-based setup is effectively an encoding of a normalized setup.
Despite that, it is doubtful that that such an encoding has substantial benefits
over other encodings. After all, one still needs to process a set of sets.

<!-- ======================================================================= -->
## one and only one CE per CSS

For those sets that must be required to have non-empty characteristic subsets,
one should require that these hold one and only one CE. That is because further
CEs merely increase the number of elements in one or more sets.

* if `(#css(s) > 0)` is necessary, then `(#css(s) == 1)` is required

<!-- ======================================================================= -->
## index-based CEs

Even though it would not be a necessity, one should use the index-based id
of each set as the CE of such a set.

<!-- ======================================================================= -->
## empty root sets /non-parent

A root set that has no child set may have an empty CSS. That is because there
is no relationship with another set that will have to be determined. Hence,
such a root set can effectively be empty.

<!-- ======================================================================= -->
## non-empty leaf sets /non-root

Each non-root leaf set must be required to have a non-empty CSS. That is
because it would otherwise not be possible to determine the parent set of
such a leaf set.

<!-- ======================================================================= -->
## parent sets with a CE

Since a parent set may have one and only one child set, not every parent set
can be allowed to have an empty CSS. That is because such a parent set would
then be equal to its child set. As a consequence, the resulting node tree
would end up having no node for that parent set.

Note that the index-based encoding of a total setup would therefore be
identical to its normalized version with the only difference that the
setup is not required to be provided as an ordered sequence.

<!-- ======================================================================= -->
## parent sets with no CE

Since a parent set that has more than one child set must contain all the CEs
of each descendant set in its inner set, and since the CE of each set is unique
to the corresponding set, the union of such CEs is itself a unique set. That
is, the CSS of a parent set that has more than one child can be required to
be empty.

<!-- ======================================================================= -->
## decoding

If the CSS of each set that can be empty is required to be empty, and if the
CSS of each set that must be required to be non-empty is required to only hold
the index-based id of the corresponding set, then such an index-based setup can
be decoded into a normalized setup such that each set has its index-based id as
its only CE.

(0) Read the ordered sequence of sets `s := (s1..sN)`.
Note that the CSS of each set must at this point have no more than one CE.

(1) Determine the rooted path `rp(si) := A*(si)` of each set.
That is, one determines the relationship of each set with all the other sets.
(Recall - DI xor RE sets - ordered by #si - RE xor OV rooted paths).

(2) For each set that has an empty CSS (i.e. if `(#css(si) == 0)`), add the
index-based id to that as the set's CE. That is, add the set's id/index to
each set in `rp(si)`.

Note that step-2 can be used to verify the setup. That is, if one determines
that the CSS of a set is non-empty and contains more than one CE, then the
setup is not as required. However, one could "fix" such a set by first
removing all the CEs of such a set. Likewise, a single pre-existing CE that
does not match the set's index-based id could be removed. In Both cases one
would treat such a set as if it had an empty CSS.
