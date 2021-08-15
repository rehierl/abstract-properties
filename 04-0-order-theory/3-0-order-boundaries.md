
<!-- ======================================================================= -->
# order - boundaries

* minimal/maximal - there is no other element smaller/greater
* least/greatest - if smaller/greater than every other element

<!-- ======================================================================= -->
## minimal/maximal elements

Given a subset `S` of a poset `P := (V,<=)`, an element `(e in S)` is said to
be **minimal**, if it is not greater than another element in `S`. Likewise, an
element is said to be **maximal**, if it is not smaller than another element.

* `isMinimal(S,e)` := if (x <= e), then (e <= x) for all (x in S)
* `isMaximal(S,e)` := if (e <= x), then (x <= e) for all (x in S)

In words: If there appears to be an element `x` that might be smaller than the
assumed minimal element `e`, then both elements must be equal. After all, `e`
could otherwise not be minimal.

Note that the definition comes with a precondition. That is, another element
that can be compared with the current minimal element (i.e. `(x <= e)` is
true), must be equal to `e`. Put differently, there is no condition that
must hold, if elements `x` and `e` are incomparable. Because of that,
**any poset may have more than one minimal/maximal element**.

Note that each non-empty subset `S` of a poset has at least one minimal and
at least one maximal element. Also, multiple minimal elements are incomparable
with each other. The same applies to multiple maximal elements.

<!-- ======================================================================= -->
## least/greatest elements

Given a subset `S` of a poset `P := (V,<=)`, an element `(e in S)` is said to
be **the least element** of `S`, if it is lower than or equal to every other
element in `S`. Likewise, an element is said to be **the greatest element**
of `S`, if it is greater than or equal to every other element.

* `isLeast(S,e)` := for (e in S), (e <= x) must be true for all (x in S)
* `isGreatest(S,e)` := for (e in S), (x <= e) must be true for all (x in S)

Note that the least element is also referred to as the subset's **minimum**,
and the greatest element as the subset's **maximum**. These should however be
avoided since they are too smiliar to the descriptions "minimal elements" and
"maximal elements".

Note that a least/greatest element must be comparable to every other element
in `S` for it to exist. Because of that, such elements are not guaranteed to
exist. However, if they exist, then there is no other such element. That is,
these elements are (if they exist) unique.

Example - Assuming the parent-of semantics, then a node tree has a least
element (its root), but not necessarily also a greatest element. The latter
is because a tree may have any number of leaf nodes. Thus, only a path graph
also has a greatest element (its single leaf).

<!-- ======================================================================= -->
## infimum/supremum

Given a subset `S` of a poset `P := (V,<=)`, an element `(e in S)` is said to
be **the infimum** (aka. inf, infima) of `S`, if it is the greatest element in
`P` that is lower than or equal to all the elements in `S`. Likewise, an element
is said to be **the supremum** (aka. sup, suprema) of `S`, if it is the least
element in `P` that is greater than or equal to all the elements in `S`.

Note that neither an infimum, nor a supremum is required to be an element in `S`.

(inaccurate!) Note that the next subsequent sibling `s` of node `n` could be
described as the supremum of the induced subtree `T[n]` in the tree's preorder
trace. - One must however keep in mind, that there is more than one node order
at play, since the induced subtree is intended denote a partial suborder! That
is, `s` is incomparable to the descendants of `n` in regards to the subtree's
node order.

<!-- ======================================================================= -->
## lower/upper set

Given a subset `S` of a poset `P := (V,<=)`, then subset `S` is said to be
**an upper set** (aka. upward closed, up-set, isotone), if it contains each
element in `V` that is greater than some element in `S`. Likewise, subset `S`
is said to be **a lower set** (aka. downward closed, down-set), if it contains
each element in `V` that is lower than some element in `S`.

* `isDownSet(P,S)` := if (v <= s) for some (s in S) and (v in V), then (v in S)
* `isUpSet(P,S)` := if (s <= v) for some (s in S) and (v in V), then (v in S)

Note that these notions are similar, but not equal to open intervals. That is,
the open interval `[s,*]` can be described as an up-set that is required to
have a least element. Note however, that an up-set is in general not required
to have a least element, it may have multiple minimal elements.
