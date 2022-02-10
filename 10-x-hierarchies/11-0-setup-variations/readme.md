
# hierarchies / variations of setups

This chapter explores the **variations** that are possible when defining setups.

**Think of this chapter as** trying to see which kinds of graphs one might end
up with, if one chooses a certain set of definitions for the definition of a
setup. That is, one first freezes the related-to operator and the edges to one
of the two set-based operators (i.e. superset-of, subset-of). Then, one freezes
the unrelated case to some alternative type of relationship (i.e. disjoint,
overlapping).

Note that this chapter is difficult to follow since it is easy to misread the
subtle but important differences between two variations: One should always keep
the orientation of each edge in mind.

Note that such a variation may be to define the related-to operator using the
**subset-of** operator, rather than the superset-of operator. Likewise, the
types of relationships allowed may be restricted to the **RE-OV**. That is,
sets may be allowed to overlap each other instead of having to be disjoint
if two sets are not considered to be related with each other.

Note that **the unrelated case** (i.e. no edge between two sets) does not
necessarily mean that both sets are disjoint. That is because, depending on
the definition of a setup, two unrelated sets may be required to overlap each
other instead.

<!-- ======================================================================= -->
## remarks

Note that this chapter is **a chapter of bullet points**. That is, this content
does not contain fleshed out sentences. Instead, it focusses on lists of bullet
points intended to highlight the aspects that are essential to the corresponding
variation.

Note that no DI-RE case supports **parallel subcomponents**. That is because
no set can have disjoint supersets, which results in the corresponding case
being either downward- or upward-total, which disallows such subcomponents.
As a matter of consequence, and in order to allow parallel sub-components,
**sets must be allowed to overlap** each other.

Note that parallel subcomponents in general result in nodes having more than
one parent and therefore **multiple rooted paths** (i.e. no downward-total
node orders). In addition to that more than one such path may exist in regards
to the same root node. That is, rooted paths are **not necessarily unique**.
