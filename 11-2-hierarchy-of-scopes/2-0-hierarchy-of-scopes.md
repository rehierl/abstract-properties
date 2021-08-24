
<!-- ======================================================================= -->
# Forest/Hierarchy of scopes

Note that a family of scopes `S`, if generated from a tree `T(N,E)` using the
concept of abstract properties, is a hierarchy of scopes `H`. That is, any tree
corresponds with a hierarchy of scopes. Consequently, `S` provides a complete
definition of `T`.

<!-- ======================================================================= -->
## a forest of scopes (F)

```
|-1-----------| |-4-----|
| |-2-| |-3-| | | |-5-| |
| |---| |---| | | |---| |
|-------------| |-------|
```

A partial/total setup `S` will be referred to as **a forest of scopes**,
if the following requirements are met:

* (R1) `S` is a normalized setup of sets.

Note that "a forest of scopes" is synonymous to "a normalized setup". That is
because there are no additional requirements. Consequently, a forest of scopes
`F` may have any number of root sets.

* `(#RS(F) in [0,*])` is true

Note that an empty setup can be described as an empty forest of scopes.

<!-- ======================================================================= -->
## a hierarchy of scopes (H)

```
|-1-----------|
| |-2-| |-3-| |
| |---| |---| |
|-------------|
```

A partial/total setup `S` will be referred to as **a hierarchy of scopes**,
if the following requirements are met:

* (R1) `S` is a normalized setup of sets.
* (R2) `S` has one and only one root set.

Note that "a hierarchy of scopes" is synonymous to "a rooted normalized setup".
Consequently, a "hierarchy of scopes" `H` has as a rooted normalized setup one
root set only.

* `(#RS(H) == 1)` is (required to be) true

Note that a hierarchy `H` of scopes has the following properties:

* `(#S > 0)` - A hierarchy is always non-empty.
* `(Ø !in H)` - No set in a hierarchy is empty.
* A hierarchy is acyclic.
* All the sets in a hierarchy are "DI ex-or RE".
* Each set as no ex-or one parent set - a superset.
* Each set may have any number of child sets - subsets.
* Any ancestor has more elements than all of its descendants.
* Each set has a unique rooted path.

Note that the root set `(r in RS(H))` of a hierarchy `H` is equal to `U(H)`.
That is because it is a superset to every other set in `H`. As such it is
equal to the union of all sets in `H`.

<!-- ======================================================================= -->
## set of all hierarchies (UH) and forests (UF)

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

Note that each hierarchy of scopes is a forest of scopes, but not necessarily
vice versa. The latter is because a setup may have more than one root set.

* forest <-> normalized setup
* hierarchy -> normalized setup

Note that two hierarchies `H1` and `H2` are **disjoint**, if their root sets
are disjoint. That is, any set in `H1` is disjoint to every set in `H2`.

* `(H1 disjoint-to H2) <-> (r1 disjoint-to r2)`

Note that any **subset** of a hierarchy, after normalizing the result, is in
general a forest - i.e. not necessarily a hierarchy. The subset will only be
a hierarchy, if the subset contains the root set of the source hierarchy.

Note that a forests and a hierarchies are both **flat**"** setups of sets.
Based on that, a forest can be described as "a union of disjoint hierarchies".

Note that the definition of a hierarchy does not cover the process of forming
the sets it contains. It merely describes how these need to be related with
each other. That is, the sets in a hierarchy may be formed in any number of
different ways. However, the description as "a hierarchy of scopes" does point
out the main method - based on the scopes of abstract properties.
