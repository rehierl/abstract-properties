
<!-- ======================================================================= -->
# Forest/Hierarchy of rpaths

Note that a family of rooted paths `S`, if generated from a tree `T(N,E)`,
is a hierarchy of rooted paths `H`. That is, any tree corresponds with a
hierarchy of rooted paths. Consequently, `S` provides a complete definition
of `T`.

<!-- ======================================================================= -->
## a forest of rpaths (F)

```
a forest of scopes             a forest rpaths
=========================  =>  ===============
|-1-----------| |-4-----|      s1: (1)
| |-2-| |-3-| | | |-5-| |      s2: (1,2)
| |---| |---| | | |---| |      s3: (1,3)
|-------------| |-------|      s4: (4)
                               s5: (4,5)
```

A partial setup `S` will be referred to as **a forest of rpaths**,
if the following requirements are met:

* (R1) `S` is a normalized setup of rooted paths.

Note that "a forest of rpaths" is synonymous to "a normalized partial setup of
rpaths". That is because there are no additional requirements. Consequently,
a forest of rooted paths `F` may have any number of rooted paths as its roots.

* `(#RS(F) in [0,*])` is true

Note that an empty setup can be described as an empty forest of rooted paths.

<!-- ======================================================================= -->
## a hierarchy of rpaths (H)


```
a hierarchy of scopes      a hierarchy of rpaths
=====================  =>  =====================
|-1-----------|            s1: (1)
| |-2-| |-3-| |            s2: (1,2)
| |---| |---| |            s3: (1,3)
|-------------|
```

A partial/total setup `S` will be referred to as **a hierarchy of rpaths**,
if the following requirements are met:

* (R1) `S` is a normalized setup of rooted paths.
* (R2) `S` has one and only one root.

Note that "a hierarchy of rooted paths" is synonymous to
"a rooted normalized setup of rpaths".

* `(#RS(H) == 1)` is (required to be) true

Note that a hierarchy `H` of rooted paths has the following properties:

* `(#S > 0)` - A hierarchy is always non-empty.
* `(Ø !in H)` - No path in a hierarchy is empty.
* A hierarchy is acyclic.
* All the paths in a hierarchy are "RE ex-or OV".
* Each path has no ex-or one parent - a prefix.
* Each path may have any number of overlapping child paths.
* Any ancestor has fewer elements than all of its descendants.
* Each path has a unique rooted path.

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

Note that a hierarchy of rooted paths is a forest of rooted paths, but not
necessarily also vice versa. The latter is because a setup may have more than
one root.

* forest <-> normalized setup
* hierarchy -> normalized setup

Note that two hierarchies `H1` and `H2` are **disjoint**, if their universal
sets are disjoint. Based on that, any path in `H1` is disjoint to every set
in `H2`.

* `(H1 disjoint-to H2) := (U(H1) disjoint-to U(H2))`

Note that an arbitrary subset of a hierarchy is neither a hierarchy, nor a
forest of hierarchies. That is because such an arbitrary subset is not required
to include each prefix of the rooted paths it contains.

Note that, except for the required prefixes, the definition of a hierarchy does
not cover the process of forming the paths it contains. It merely describes how
these are related with each other. That is, the sequences in a hierarchy may be
formed in any number of different ways. However, the description as "a hierarchy
of rooted paths" does highlight the main method - i.e. contains all the rooted
paths of a node tree.
