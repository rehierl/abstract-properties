
<!-- ======================================================================= -->
# prefix, infix, suffix over posets

As mentioned in the recap of mathematical concepts, the substring of a sequence
can be understood to be defined based upon the underlying index-order.

Note that the following is inteded to provide a more intuitive way to look at
posets: based on terms that are known in the context of sequences. In regards
to the overall discussion it is sufficient to look at an induced subtree as
a suffix to the super-tree and the underlying poset.

<!-- ======================================================================= -->
## sequences - index-based intervals

Due to the above, interval-based definitions can be provided for the terms
"infix", "prefix" and "suffix".

* for some sequence `s` and indexes `(a,b in [1,#s])`
* `(t infix-of s), (t substring-of s) := (t == s[a,b])`
* `(t prefix-of s) := (t == s[*,b])` - a down-set
* `(t suffix-of s) := (t == s[a,*])` - an up-set

In words: A sequence `s` can be described as a substring, if it can be expressed
in terms of an index-based interval over the index-order of the corresponding
sequence.

With the above generalized perspective on intervals over posets, the default
notion of these terms can be understood to shift away from "(induced) substrings
over sequences" towards "(induced) suborders over posets" that have certain
characteristics. That is, regardless of whether the source orders is total
or not.

<!-- ======================================================================= -->
## tosets - element-based intervals

Recall that a total order can be defined using an ordered sequence. That is
because an ordered sequence contains no element more than once and because,
based upon its total index-order, an ordered sequence can be understood to
associate a unique index with each element.

In case the source order is a total order, the meaning of the above terms
remains almost unchanged. After all, the then **element-based intervals**
in regards to an ordered sequence can then still be understood to denote
substrings.

* for some ordered sequence `s` and elements `(e,f in E(s))`
* `(t infix-of s), (t substring-of s) := (t == s[e,f])`
* `(t prefix-of s) := (t == s[*,e])`
* `(t suffix-of s) := (t == s[f,*])`

Since each element endpoint `e` in such an interval can be understood to first
be replaced by its unique index `idx(e)`, these element-based intervals can
still be understood to **correspond with index-based intervals**.

* `s[e,f] <=> s[idx(e),idx(f)]`

<!-- ======================================================================= -->
## posets - suffix - (e,*)

However, since a partial order has no (total) index order associated with it,
the index-based perception of "suffix" no longer applies. Because of that,
one nees to recall the essence of its definition.

In regards to an ordered sequence `s`, **a suffix** begins with an element and
contains every other element that is subsequent to it. Based on that, one can
conclude that a suffix is also a suffix to another suffix that has more elements.
After all, each total order has one and only one sink vertex.

* for `s1 := s[e,*]` and `s2 := s[f,*]`
* `(s2 suffix-of s1)` if `(idx(f) >= idx(e))`
* `(s2 suffix-of s1)` if `(f >= e)`

Note that the elements `e` and `f` can in general be described as
**offset elements**.

As such, this basic definition still applies to partial orders. However,
one needs to keep in mind that, in contrary to a total order, a partial order
`p` may have any number of sink vertices (hint - leaf nodes). Consequently,
any partial order may have **disjoint** suffixes.

* for `p1 := p[e,*]` and `p2 := p[f,*]`
* `(p2 suffix-of p1)` is true if `(f >= e)`
* `(E(p2) disjoint-to E(p1))` is true if `(f incomparable-to e)`

Note that the overall focus of this discussion will be on suffixes that are
induced by one and only element of an ordered set. That is, the focus will be
on suffixes that can be expressed in terms of element-based open intervals.

Note that any such suffix over a poset may be an induced total or partial
suborder (i.e. a sub-toset or a sub-poset). That is, any such suffix may
or may not contain incomparable elements.

Note that this one-element based perspective on suffixes over posets can in
principle be extended to cover suffixes that are defined based upon more than
one offset element. That is, a sub-forest of disjoint induced subtrees can be
described as a suffix to the super-tree.

Note that such a sub-forest can still be described as "an up-set".

<!-- ======================================================================= -->
## posets - prefix - (p \s*)

In regards to an ordered sequence `s`, **a prefix** can be formed, if a suffix
is removed. Similar as before, and in the context of ordered squences, any
prefix is a prefix to another prefix that has more elements.

* `(s2 prefix-of s)` if `s2 := (s \ s1)` for some `(s1 suffix-of s)`

In words: The suborder of a poset can be described as a prefix to the poset,
if it can be formed by removing zero, one or more suffixes.

As such, this basic definition can still be understood to apply to a partial
order `p`. That is, the prefix of a partial order is formed by the removal
of a (possibly empty) suffix. Once again, one needs to keep in mind that,
in contrary to a total order, a partial order may in general have any number
of source vertices (hint - a forest of trees, i.e. not necessarily a single
tree). Consequently, any partial order may in general have prefixes that are
**disjoint** and even prefixes that **overlap** each other.

* for `(pe,pf prefix-of p)`
* `(pe related-to ps)` may be true
* `(pe disjoint-to pf)` may be true
* `(pe overlaps pf)` may be true

As before any such prefix over a poset may be an induced total or partial
suborder. That is, any such prefix may itself contain incomparable elements.
(hint - a rooted path in a tree is just a special prefix of the tree).

Note that the prefix of a tree is itself a rooted tree. That is, a tree and
all of its prefixes have the same root node.

<!-- ======================================================================= -->
## posets - infix - (p \s* \p*)

In regards to an ordered sequence `s`, **an infix** can be formed,
if a suffix and/or a prefix is removed.

* for some `(s1 suffix-of s)` and `(s2 prefix-of s)`
* `(s3 infix-of s)` if `sf := ((s \s1) \s2)`

In words: The suborder of a poset can be described as an infix to the poset,
if it can be formed by removing prefixes and/or suffixes.

Note that distinct infixes in regards to the same poset may be related,
disjoint, and even overlap each other.
