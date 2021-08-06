
<!-- ======================================================================= -->
# prefix, infix, suffix over posets

As mentioned in the recap of mathematical concepts, the substring of a sequence
can be understood to be defined based upon the index-order of that sequence.
Based on that, interval-based definitions for the terms "infix", "prefix" and
"suffix" can be provided.

* for some sequence `s` and indexes `(a,b in [1,#s])`
* `(t infix-of s), (t substring-of s) := (t == s[a,b])`
* `(t prefix-of s) := (t == s[*,b])`
* `(t suffix-of s) := (t == s[a,*])`

Note that, with the generalized perspective on intervals over posets, the
default notion of these terms can be understood to shift away from "(induced)
substrings over sequences" towards "(induced) suborders over posets" that have
certain characteristics. That is, regardless of whether these source orders
are total or not/partial.

<!-- ======================================================================= -->
## prefix, infix, suffix over tosets

Recall that any total order can be defined based upon an ordered sequence.
That is because an ordered sequence contains no element more than once and
because, based upon its index-order, an ordered sequence can be understood
to associate a unique index with each element.

In case the source order is a total order, the meaning of the above terms
remains almost unchanged. After all, the then element-based intervals in
regards to an ordered sequence can then still be understood to denote
substrings.

* for some ordered sequence `s` and elements `(e,f in E(s))`
* `(t infix-of s), (t substring-of s) := (t == s[e,f])`
* `(t prefix-of s) := (t == s[*,f])`
* `(t suffix-of s) := (t == s[e,*])`

Since each element endpoint `e` can be understood to first be replaced by its
unique index `idx(e)`, these element-based intervals can still be understood
to translate to index-based intervals.

* `s[e,f] <=> s[idx(e),idx(f)]`

<!-- ======================================================================= -->
## suffixes over posets

However, since a partial order has no (total) index order associated with it,
the index-based perception of "suffix" no longer applies. Because of that, one
nees to recall the essence of that term.

In regards to an ordered sequence `s`, **a suffix** begins with a given element
and contains every other element that is subsequent to it. Based on that, one
can conclude that a suffix is also a suffix to another suffix that has more
elements. After all, each total order has one and only one sink vertex.

* for `se := s[e,*]` and `sf := s[f,*]`
* `(sf suffix-of se)` if `(idx(e) <= idx(f))`
* `(sf suffix-of se)` if `(e <= f)`

Note that the elements `e` and `f` can each be described as
**an offset element**.

As such, this basic definition still applies to partial orders. However, one
needs to keep in mind that, in contrary to a total order, a partial order `p`
may in general have any number of sink vertices (hint - think in terms of leaf
nodes). Consequently, any partial order may in general have suffixes that are
**disjoint**.

* for `pe := p[e,*]` and `pf := p[f,*]`
* `(pf suffix-of pe)` is true if `(e <= f)`
* `(E(pf) disjoint-to E(pe))` is true if `(f incomparable-to e)`

Note that the overall focus of this discussion will be on suffixes that are
induced by one and only element of an ordered set. That is, the focus will
be on suffixes that can be expressed in terms of an open interval.

Note that any such suffix over a poset may be an induced total or partial
suborder (i.e. a sub-toset or a sub-poset). That is, any such suffix may
still contain incomparable elements.

Note that this one-element based perspective on suffixes over posets can in
principle be extended to cover suffixes that are defined based upon more than
one offset element. That is, a sub-forest of induced subtrees can be described
as a suffix to the super-tree.

<!-- ======================================================================= -->
## prefixes over posets

In regards to an ordered sequence `s`, **a prefix** can be formed, if a
suffix is removed. Similar to before, and in the context of ordered squences,
any prefix is a prefix to any other prefix that has more elements.

* `(sf prefix-of s)` if `sf := (s \ se)` for some `(se suffix-of s)`
* `(sf prefix-of sg)` if `(#sf <= #sg)` for some `sf,sg prefix-of s`

As such, this basic definition can still be understood to apply a partial
order `p`. That is, the prefix of a partial order is formed by the removal
of a (possibly empty) suffix. Once again, one needs to keep in mind that,
in contrary to a total order, a partial order may in general have any number
of source vertices (hint - a forest of trees, i.e. not necessarily a single
tree). Consequently, any partial order may in general have prefixes that are
**disjoint** and even prefixes that **overlap** each other.

* for `(pe,pf prefix-of p)`
* `(pe disjoint-to pf)` and `(pe overlaps pf)` may be true

As before any such prefix over a poset may be an induced total or partial
suborder. That is, any such prefix may itself contain incomparable elements.
(hint - a rooted path in a tree is just a special prefix of the tree).

Note that the prefix of a tree is itself a rooted tree. That is, a tree and
all of its prefixes have the same root node.

<!-- ======================================================================= -->
## infixes over posets

In regards to an ordered sequence `s`, **an infix** can be formed,
if a suffix and/or a prefix is removed.

* for some `(se prefix-of s)` and `(sg suffix-of s)`
* `(sf infix-of s)` if `sf := ((s \ se) \ sg)`

As such, this basic definition can still be understood to also apply to
a partial order `p`.

Note that distinct infixes in regards to the same poset may be related,
disjoint, and even overlap each other.
