
<!-- ======================================================================= -->
# Forest/Hierarchy of strings

Note that the following definitions of forests/hierarchies of strings must be
understood to be in preparation of more specific hierarchies of strings. That
is, a generic type of hierarchy of strings is such that there is no requirement
as to how the strings it contains must be formed. Specialized hierarchies will
then be defined that specify the kinds of strings, and how these must be related
with each other.

<!-- ======================================================================= -->
## a forest of strings (F)

A partial setup of strings `S` may be referred to as **a forest of strings**,
if the following requirements are met.

* (R0) `S` is a partial setup of strings.
* (R1) There are `#s` substrings for each string `(s in S)`

Recall that a partial setup `S` covers the **DI-RE** case. Because of that,
a forest of strings `F` may only contain disjoint ex-or related strings.

Note that requirement R1 is intended to state that for each string `(s in S)`
there must be `#s` distinct substrings in `S`, one for each node in `s`.
As such, that R1 can be understood to be analogous to "Each set in a setup
of sets must have one and only one CE".

Note that a forest of strings may have any number of root strings, including
none at all.

* `(#RS(F) in [0,*])` is true

<!-- ======================================================================= -->
## a hierarchy of trees (H)

A partial setup `S` may be referred to as **a hierarchy of strings**,
if the following requirements are met.

* (R0) `S` is a forest of strings.
* (R1) `S` has one and only one root.

Note that a hierarchy of strings `H` has the following properties:

* `(#RS(H) == 1)` must be true
* The root string`r` is equal to `U(H)`.
* `(#S > 0)` - A hierarchy is always non-empty.
* All the strings in a hierarchy are "DI ex-or RE".
* Each string has no ex-or one parent - a superstring.
* Each string may have any number of child strings - substrings.
* Any ancestor has more nodes than all of its descendants.
* Each string has a unique rooted path.

<!-- ======================================================================= -->
## set of all hierarchies and forests

Similar to hierarchies and forests of sets, a theoretical set of all possible
hierarchies **UH** and a theoretical set of all possible forests **UF** can
be assumed to exist.

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in UH)` states that `h` is expected to be
a hierarchy. Likewise, `(f in UF)` states that `f` is expected to be a forest
of strings.

* `(UH proper-subset-of UF)`
