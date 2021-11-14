
<!-- ======================================================================= -->
# Forest/Hierarchy of scopes

Note that a family of scopes `S`, if generated from a tree `T(N,E)` using the
concept of abstract properties, is a hierarchy of scopes `H`. That is, any tree
is isomorphic to a setup of scopes `S`.

<!-- ======================================================================= -->
## a forest of scopes (F)

```
|-1-----------| |-4-----|
| |-2-| |-3-| | | |-5-| |
| |---| |---| | | |---| |
|-------------| |-------|
```

A partial setup `S` may be referred to as **a forest of scopes**,
if the following requirements are met:

* (R0) `S` is a normalized setup of sets.

Note that a forest of scopes may have any number of root sets,
including none at all.

* `(#RS(F) in [0,*])` is true

Note that a forest of scopes has no additional requirements. Because of that,
a forest of scopes `F` may only contain disjoint ex-or related scopes. (i.e.
the **DI-RE** case).

<!-- ======================================================================= -->
## a hierarchy of scopes (H)

A partial setup `S` may be referred to as **a hierarchy of scopes**,
if the following requirements are met:

* (R0) `S` is a forest of scopes.
* (R1) `S` has one and only one root.

Note that a hierarchy of scopes `H` has the following properties:

* `(#RS(H) == 1)` must be treu
* `(#S > 0)` - A hierarchy is always non-empty.
* `(Ø !in H)` - No set in a hierarchy is empty.
* All the sets in a hierarchy are "DI ex-or RE".
* Each set has no ex-or one parent set - a superset.
* Each set may have any number of child sets - subsets.
* Any ancestor has more elements than all of its descendants.
* Each set has a unique rooted path.

Note that the root set `(r in RS(H))` of a hierarchy `H` is equal to `U(H)`.
Despite that, the root set of a hierarchy is required as an explicit set since
even the root set must have a CE, which can not be an element in another set.
That is, there must be one element in `U(H)` which is an element only in the
hierarchy's root set.

* `(r == U(H))` is true

<!-- ======================================================================= -->
## set of all hierarchies and forests

The theoretical **set of all possible hierarchies (UH)** and the theoretical
**set of all possible forests (UF)** can be defined as follows:

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in UH)` states that `h` is expected to be
a hierarchy. Likewise, `(f in UF)` states that `f` is expected to be a forest
of hierarchies.

* `(UH proper-subset-of UF)`

<!-- ======================================================================= -->
## remarks

Note that a hierarchy of scopes is a forest of scopes, but not necessarily also
vice versa. The latter is because a partial setup may in general have more than
one root set.

* forest <-> normalized setup
* hierarchy -> normalized setup

Note that two hierarchies `H1` and `H2` are **disjoint**, if their root sets
are disjoint. Based on that, any set in `H1` is disjoint to each set in `H2`.

* `(H1 disjoint-to H2) := (r1 disjoint-to r2)`

Note that an arbitrary **subset** of a hierarchy, after normalizing the result,
is in general a forest - i.e. not necessarily a hierarchy.
