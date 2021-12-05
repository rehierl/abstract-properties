
<!-- ======================================================================= -->
# Forest/Hierarchy of strings

As before with setups of trees, specialized but still generic forests and
hierarchies of strings can be defined as follows.

<!-- ======================================================================= -->
## a forest of strings (F)

A partial setup of strings `S` may be referred to as **a forest of strings**,
if the following requirements are met.

* (R0) `S` is a partial setup of strings.
* (R1) There are `#s` substrings for each string `(s in S)`

Recall that the related-to operator of a partial setup `S` is defined based
on the **superstring-of** operator and that such a setup covers the **DI-RE**
case. Because of that, a forest of strings `F` may only contain disjoint
ex-or related strings.

Note that requirement R1 is intended to state that for each string `(s in S)`
there must be `#s` distinct substrings in `S`, one for each node in it. As
such, requirement R1 can be understood to be analogous to "Each set in a
setup of sets must have one and only one CE".

Note that even though a substring is not even required to be a prefix or a
suffix, in the context of this discussion, substrings will be required to be
prefixes or suffixes to their superstrings.

Note that a forest of strings may have any number of root strings, including
none at all.

* `(#RS(F) in [0,*])` is true

<!-- ======================================================================= -->
## a hierarchy of strings (H)

A partial setup `S` may be referred to as **a hierarchy of strings**,
if the following requirements are met.

* (R0) `S` is a forest of strings.
* (R1) `S` has one and only one root.

Note that a hierarchy of strings `H` has the following properties:

* `(#RS(H) == 1)` must be true
* `(#S > 0)` - A hierarchy is always non-empty.
* Each string has no ex-or one parent - a superstring.
* Each string may have any number of child strings - substrings.
* Any ancestor has more nodes than all of its descendants.
* Each string has a unique rooted path of strings.
* the root string `r` is equal to `G(H)`.

<!-- ======================================================================= -->
## set of all hierarchies and forests

Similar to hierarchies and forests of sets, a theoretical set of all possible
hierarchies (UH) and a theoretical set of all possible forests (UF) can be
assumed to exist.

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in UH)` states that `h` is expected to be
a hierarchy. Likewise, `(f in UF)` states that `f` is expected to be a forest
of strings.

* `(UH proper-subset-of UF)`
