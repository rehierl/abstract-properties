
<!-- ======================================================================= -->
# index-based setups

Even though an ordered sequence of elements can be understood to define an
index-based order over the elements in it, the use of an **ordered sequence**
to define a setup of sets is not for the index-based order to apply to the
sets themselves, but to define **index-based ids** for the sets in it.

These ids can then be used to lookup the corresponding node in an ordered
sequence of node definitions (i.e. an index-based mapping) that needs to be
understood to be provided separately, alongside the ordered sequence of sets.

When choosing to provide numeric index-based ids via the index-order of an
ordered sequence of sets, one would certainly want to first **reduce** the
amount of elements in each set to a bare minimum. The following will mention
the aspects one should keep in mind.

Note that, due to the below, an index-based setup is effectively an encoding
of a normalized setup. Despite that, it is doubtful that such an encoding has
substantial benefits over other encodings.

<!-- ======================================================================= -->
## no more than one CE per CSS

In case there is a set `s` that has a CSS such that  `(#css(s) > 1)` one can
reduce the CSS by removing any additional CE from each set in `rp(s) := A*(s)`.

<!-- ======================================================================= -->
## index-based CEs

Even though it would not be a necessity, one should use the index-based id
of each set as the CE of such a set.

In case set `s` has a non-index CE, one should remove `ce(s)` from each set
in `rp(s)` and then add `id(s)` to these sets in its stead.

<!-- ======================================================================= -->
## empty root sets /non-parent

A root set that has no child set may have an empty CSS. That is because there
is no relationship with another set that will have to be determined. Hence,
such a root set can reduced to the empty set.

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

Note that the index-based encoding of a total setup will thus be identical to
its normalized version with the only difference that the setup is not required
to be provided as an ordered sequence.

<!-- ======================================================================= -->
## parent sets with no CE

Since a parent set that has more than one child set must contain all the CEs
of each descendant set in its inner set, the inner set of such a parent set
is itself a unique set. Because of that, each CE of such a parent set can be
removed.

<!-- ======================================================================= -->
## decoding

If the CSS of each set that can be empty is required to be empty, and if the
CSS of each set that must be non-empty is required to only hold the index-based
id of the corresponding set, then such an index-based setup can be decoded into
a normalized setup such that each set has its index-based id as its only CE.

(0) Read the ordered sequence of (minimized) sets `s := (s1..sN)`.
Note that the CSS of each set must at this point have no more than one CE.

(1) Determine the rooted path `rp(s) := A*(s)` of each set.
That is, one determines the relationship of each set with all the other sets.
(Recall - DI xor RE for sets - ordered by #s - RE xor OV for rooted paths).

(2) For each set that has an empty CSS (i.e. `(#css(s) == 0)`),
add `id(s)` to each set in `rp(s)`.

Note that step-2 can be used to verify the setup. That is, if one determines
that the CSS of a set is non-empty and contains more than one CE, then the
setup is not as required. However, one could "fix" such a set by first
removing all the CEs of such a set. Likewise, a single pre-existing CE that
does not match the set's index-based id could be removed. In Both cases one
would treat such a set as if it had an empty CSS.

Note however that it stands to reason whether or not it would be better to
simply reject any malformed input setup.
