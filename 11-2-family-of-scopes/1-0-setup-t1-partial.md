
<!-- ======================================================================= -->
# A partial setup (of type-1)

Recall that a partial setup (T1) `S` has the following requirements:

* (R1) No set in `S` may be empty.
* (R2) Any two sets in `S` must either be disjoint ex-or related.

Note that the focus of this chapter is on rooted setups.
That is, setups which have one and only one root set.

<!-- ======================================================================= -->
## partial setup => partial order

```
S: a partial setup                              S: a partial setup
=========================================  <=>  ==================
|-A-------------------------------------|       S := {
| |-B-----------| |-E-| |-F-----------| |         A: { 1, 2, 3, 4, 5 },
| | |-C-| |-D-| | | 3 | | |-G-| |-H-| | |         B: { 1, 2          },
| | | 1 | | 2 | | |---| | | 4 | | 5 | | |         C: { 1             },
| | |---| |---| |       | |---| |---| | |         D: {    2          },
| |-------------|       |-------------| |         E: {       3       },
|---------------------------------------|         F: {          4, 5 },
                                                  G: {          4    },
                                                  H: {             5 } }
```

Note that, except for leaf sets, no set has a characterisitc element.
That is, the CSS of sets A, B, and F are empty.

* i.e. `(css(s) == Ø)` for `(s in {A,B,F})`

Since one can (randomly) iterate over the sets in `S`, and since each set
`(s in S)` is different to every other set in `S`, one can define a set of
identifiers `ID` such that it holds a unique id for each set in `S`. Based on
being able to test simple sets for equality, one can then define a bijective
function `id(s)` such that it returns the id of the given set, and also a
bijective function `set(id)` such that it returns the set that is associated
with the given id.

* `ID := {A..H}`
* `id(s)` := returns the `(id in ID)` of set `s`
* `set(id)` := returns the set `(s in S)` that has the given id
* `id()` is inverse to `set()`

Using the above rooted setup `S`,
one can define a partial order over `S`.

* `P(S,<)` where ..
* `(a < b) := (a superset-of b) for (a,b in S)`

Since one can associate an id with each set,
one can also define a partial order over `ID`.

* `P(ID,<)` where `ID := {A..H}`
* `(id(a) < id(b)) := (a superset-of b) for (a,b in S)`

<!-- ======================================================================= -->
## partial setup => node tree

```
S: a partial setup                             T: a node tree
=========================================  =>  ==============
|-A-------------------------------------|            A        |- superset-of
| |-B-----------| |-E-| |-F-----------| |         -------     |
| | |-C-| |-D-| | | 3 | | |-G-| |-H-| | |         B  E  F     |
| | | 1 | | 2 | | |---| | | 4 | | 5 | | |      ----     ----  |
| | |---| |---| |       | |---| |---| | |      C  D     G  H  |- subset-of
| |-------------|       |-------------| |
|---------------------------------------|
```

Using the above rooted setup `S`,
one can directly define a node tree over `S`.

* `T(S,E)` where ..
* `E := { (a,b) | (a parent-set-of b) for (a,b in S) }`

Since one can associate an id with each set,
one can also directly define a node tree over `ID`.

* `T(ID,E)` such that `ID := {A..H}` and ..
* `E := { (id(a),id(b)) | (a parent-set-of b) for (a,b in S) }`

Note that a partial setup has no other requirements that could be used to form
a node tree. That is, the only information available that can be used are the
relationships between the sets in `S`. Consequently, the resulting tree has one
node per set (i.e. `(#N == #S)`), not one node per element in `U(S)` (i.e.
`(#N != #U(S))` - i.e. 8 nodes, not 5 nodes). Put differently, a setup of `#S`
will yield a node tree of `#S` nodes.

* `#S => #N`

Note that one could increase the CSS of each set without changing the amount of
nodes and also without affecting the tree's structure. That is, even if the CSS
of each set would be (e.g.) a 2-element set, the resulting tree would still be
as shown above (i.e. a tree with `#S`) nodes. (Note that, in order to increase
`css(s)` one needs to add a unique element to each set in `A*(s)`).

<!-- ======================================================================= -->
## conclusion

Even though the relationship a node has with all the other nodes is defined
by those elements that are shared by the sets in `S`, the translation of a
set into a node is independent of these elements. That is, a setup does thus
far not embed the definition of the nodes themselves.

As shown above, one can still associate a unique id with each set. However,
since the iteration over the sets in `S` is random, subsequent runs will
produce trees that have the same structure, but will in general also produce
trees whose nodes differ in their labels (i.e. their id values). For obvious
reasons, this randomness is insufficient since the intention is to reliably
recreate a tree from a setup of sets.

Note that the question is not how to embed the objects themselves, but how
to embed unique object/node identifiers such that one can reliably determine
the identifier that is associated with a particular set.

For obvious reasons, further requirements must be introduced such that a
setup can be understood to provide the complete definition of a node tree.

Due to the above, one available option is to provide a setup of sets as
**an ordered sequence of sets**. That is because the index-order can then be
understood to provide a unique id for each set - i.e. **implicit embedding**.
Using this method, one would however be restricted to index-based id values.

Since the elements in `U` have no direct effect on the structure of the
resulting tree, a different option that is available would be to require
that each element in `U` is an object id. After all, each element in `U`
is **a characteristic element** and as such unique to the corresponding
characteristic subset - i.e. **explicit embedding**. In contrary to before,
and even though one will in general use index-based ids, one could choose
to use non-numeric ids.
