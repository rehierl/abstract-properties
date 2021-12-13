
<!-- ======================================================================= -->
# Forest/Hierarchy of rooted paths

Forests and hierarchies of rooted paths can be defined as follows.

<!-- ======================================================================= -->
## a forest of rpaths (F)

```
a forest of scopes             a forest of rpaths
=========================  =>  ==================
|-1-----------| |-4-----|      s1: (1)
| |-2-| |-3-| | | |-5-| |      s2: (1,2)
| |---| |---| | | |---| |      s3: (1,3)
|-------------| |-------|      s4: (4)
                               s5: (4,5)
```

A set of rooted paths `S` may be referred to as **a forest**,
if the following requirements are met.

* (R0) `S` is a partial setup of rpaths.
* (R1) `S` must include every prefix of each path `(s in S)`.

Note that the paths in a forest of rooted paths may be disjoint (DI),
related (RE), or overlap each other (OV) - i.e. the **DI-RE-OV** case.

Recall that, desipte the modified related-to operator (i.e. prefix-of) and
the relationships allowed (i.e. DI-RE-OV), a forest of rooted paths can
still be described as a setup of strings.

<!-- ======================================================================= -->
## remarks on requirement R1

Due to requirement R1, a partial setup of rooted paths may be described as
being **downward-closed** in the sense that there is no element missing that
could be derived from any pre-existing path. (Note - "closed" in the sense
of a "transitive closure").

* `(S(s) subset-of S)` is true for all `(s in S)` where ..
* `S(s) := { t | (t prefix-of s) and (#t > 0) }`

Requirement R1 is a necessity since it ensures that each path has one and
only one characteristic element **CE**. That is, the characteristic element
`ce(s)` of each path in a forest its **last node**.

* `(#css(s) == 1)` is true for any `(s in S)`
* `ce(s) := s[#s]` for any `(s in S)`
* `(CE(S) == U(S))` is true

Since a forest is required to hold all the prefixes of every path in it,
any **root** path in it is a rooted path of length 1.

* `(#r == 1)` for any `(r in RP(S))`

The amount of rooted paths in `A(s)` is no longer arbitrary. That is because
a forest must contain all the prefixes of every path in it. Any **child**
therefore has one more element in addition to its parent, which is why
**siblings** have the same length.

* `(#A(s) == (#s-1))` is true for any `(s in S)`
* `(#c == #p+1)` if `(p parent-of c)`
* `(#s1 == #s2)` if `(s1 sibling-of s2)`

The intersection between any two rooted paths in `S` is either empty
or a rooted path in that setup.

<!-- ======================================================================= -->
## a hierarchy of rpaths (H)

A set of rooted paths `S` may be referred to as **a hierarchy**,
if the following requirements are met.

* (R0) `S` is a forest of rpaths.
* (R1) `S` has one and only one root.

Note that a hierarchy of rpaths `H` has the following properties.

* `(#RP(S) == 1)` and `(#S > 0)` must be true.
* Each path has no ex-or one parent - a prefix.
* Each path may have any number of child paths - overlapping.
* Each path has a unique rooted path (of rooted paths).
* Any ancestor has fewer elements than all of its descendants.
* The root path `r` in a setup is a path of one node only.

Note that, since a hierarchy is required to have one and only one root, the
rooted paths in a hierarchy of rooted paths are not allowed to be disjoint -
i.e. the **RE-OV** case. That is because the root of a hierarchy is a prefix
to all the paths in that hierarchy.

<!-- ======================================================================= -->
## remarks

Two arbitrary hierarchies `H1` and `H2` are **disjoint**, if and only if their
universal sets of elements are disjoint. It is insufficient to only test the
root nodes of two paths in both hierarchies since both paths might still
intersect each other in some other node.

* `(H1 disjoint-to H2) := (U(H1) disjoint-to U(H2))`
* `(p1[1] == p2[1]) -> (H1 coupled-with H2)` for `(p1 in H1)` and `(p2 in H2)`
* `(p1[1] != p2[1]) =?> (H1 disjoint-to H2)`

Note that even though both hierarchies are themselves required to be well formed,
the order defined by hierarchy H1 might still be in conflict with the order of
hierarchy H2. However, if both hierarchies can be understood to form a forest
of hierarchies, then it would be sufficient to only test the first nodes of two
paths for equality.

Note that an arbitrary **subset** of a hierarchy is neither guaranteed to be
a hierarchy, nor a forest. That is because an arbitrary subset is not required
to include all the prefixes of each paths it contains.
