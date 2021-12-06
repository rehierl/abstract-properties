
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

A set of rooted paths `S` may be referred to as **a forest of rpaths**,
if the following requirements are met.

* (R0) `S` is a partial setup of rpaths.

Note that the paths in a forest of rooted paths may be disjoint (DI),
related (RE), or overlap each other (OV) - i.e. the **DI-RE-OV** case.

Recall that, desipte the modified related-to operator (i.e. prefix-of) and
the relationships allowed (i.e. DI-RE-OV), a forest of rooted paths can be
described as a setup of strings.

<!-- ======================================================================= -->
## a hierarchy of rpaths (H)

A set of rooted paths `S` may be referred to as **a hierarchy of rpaths**,
if the following requirements are met.

* (R0) `S` is a partial setup of rpaths.
* (R1) `S` has one and only one root.

Note that a hierarchy of rpaths `H` has the following properties.

* `(#RP(h) == 1)` must be true.
* `(#S > 0)` - A hierarchy is always non-empty.
* Each path has no ex-or one parent - a prefix.
* Each path may have any number of child paths - overlapping.
* Each path has a unique rooted path (of rooted paths).
* Any ancestor has fewer elements than all of its descendants.
* The root path `r` in a setup is a path of one node only.

Note that, since a hierarchy is required to have one and only one root, the
rooted paths in a hierarchy of rooted paths are not allowed to be disjoint -
i.e. the **RE-OV** case.

<!-- ======================================================================= -->
## remarks

Note that two hierarchies `H1` and `H2` are **disjoint**, if and only if their
universal sets of elements are disjoint. It is insufficient to only test the
root nodes of the paths in both hierarchies since the paths in both hierarhcies
might still intersect each other in some other node.

* `(H1 disjoint-to H2) := (U(H1) disjoint-to U(H2))`

Note that an arbitrary **subset** of a hierarchy is neither guaranteed to be
a hierarchy, nor a forest. That is because an arbitrary subset is not required
to include all the prefixes of all the paths it contains.
