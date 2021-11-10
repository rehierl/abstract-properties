
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

Note that a forest of scopes has no additional requirements. Because of that,
a forest of scopes `F` may have any number of root sets, which is why an empty
setup may be described as "an empty forest of scopes".

* `(#RS(F) in [0,*])` is true

<!-- ======================================================================= -->
## a hierarchy of scopes (H)

```
|-1-----------|
| |-2-| |-3-| |
| |---| |---| |
|-------------|
```

A partial setup `S` may be referred to as **a hierarchy of scopes**,
if the following requirements are met:

* (R0) `S` is a normalized setup of scopes.
* (R1) `S` has one and only one root set `r`.

Note that "a hierarchy of scopes" is synonymous to "a rooted normalized partial
setup" and also synonymous to "a rooted forest of scopes".

* `(#RS(H) == 1)` is required to be true

Note that a hierarchy of scopes `H` has the following properties:

* `(#S > 0)` - A hierarchy is always non-empty.
* `(Ø !in H)` - No set in a hierarchy is empty.
* A hierarchy is acyclic.
* All the sets in a hierarchy are disjoint ex-or related.
* Each set has no ex-or one parent set - a superset.
* Each set may have any number of child sets - subsets.
* Any ancestor has more elements than all of its descendants.
* Each set has a unique rooted path of sets.

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
are disjoint. Based on that, any set in `H1` is disjoint to every set in `H2`.

* `(H1 disjoint-to H2) := (r1 disjoint-to r2)`

Note that any **subset** of a hierarchy, after normalizing the result, is in
general a forest - i.e. not necessarily a hierarchy.

Note that the definition of a hierarchy does not cover the process of forming
the sets it contains. It merely describes how these are related with each other.
However, the description as "a hierarchy of scopes" does highlight the main
method - i.e. formed from the scopes of abstract properties.
