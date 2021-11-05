
<!-- ======================================================================= -->
# A partial setup (of sets)

Recall that a partial setup `S` has the following requirements:

* (1) No set in `S` is empty.
* (2) Any two sets in `S` are either disjoint ex-or related.

Note that the focus of this chapter is on rooted setups.

* `S` is a "rooted setup", iff `(#RS(S) == 1)` is true

<!-- ======================================================================= -->
## unique identifiers

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

Note that, except for leaf sets, no set in the above setup has a characteristic
element. That is, the characteristic subsets of sets A, B, and F are empty.

* `(css(s) == Ø)` for `(s in {A,B,F})`

Since one can (randomly) iterate over the sets in `S`, and since each `(s in S)`
is distinct to every other set, one can define a set of identifiers `ID` such
that it holds a unique id for each set in `S`. Based on that, a binary relation
`R(S,ID,G)`, which associates an `(id in ID)` with each set, can be defined.

* `G(R) := { (s,ID(s)) | for (s in S) }`

Based on being able to test simple sets for equality, one can define a bijective
function `ID(s)` such that it returns the id of a given set, and a bijective
function `S(id)` such that it returns the set that is associated with the given
identifier.

* `ID := {A..H}`
* `ID(s) := i` if `sRi`
* `S(i) := s` if `sRi`
* `ID(s)` is inverse to `S(i)`

<!-- ======================================================================= -->
## partial setup => partial order

```
S: a partial setup                             P: a partial order
=========================================  =>  ==================
|-A-------------------------------------|            A        |- superset-of
| |-B-----------| |-E-| |-F-----------| |         -------     |
| | |-C-| |-D-| | | 3 | | |-G-| |-H-| | |         B  E  F     |
| | | 1 | | 2 | | |---| | | 4 | | 5 | | |      ----     ----  |
| | |---| |---| |       | |---| |---| | |      C  D     G  H  |- subset-of
| |-------------|       |-------------| |
|---------------------------------------|
```

Using the above rooted setup `S`,
one can define a partial order over `S`.

* `P(S,<)` where ..
* `(a < b) := (a superset-of b) for (a,b in S)`

Since one can associate an id with each set,
one can also define a partial order over `ID`.

* `P(ID,<)` where `ID := {A..H}`
* `(ID(a) < ID(b)) := (a superset-of b) for (a,b in S)`

<!-- ======================================================================= -->
## partial setup => node tree

```
S: a partial setup                             T: a node tree
=========================================  =>  ==============
|-A-------------------------------------|            A        |- parent-of
| |-B-----------| |-E-| |-F-----------| |         -------     |
| | |-C-| |-D-| | | 3 | | |-G-| |-H-| | |         B  E  F     |
| | | 1 | | 2 | | |---| | | 4 | | 5 | | |      ----     ----  |
| | |---| |---| |       | |---| |---| | |      C  D     G  H  |- child-of
| |-------------|       |-------------| |
|---------------------------------------|
```

Using the above rooted setup `S`,
one can directly define a node tree over `S`.

* `T(S,E)` where ..
* `E := { (a,b) | (a parent-of b) for (a,b in S) }`

Since one can associate an id with each set,
one can also directly define a node tree over `ID`.

* `T(ID,E)` such that `ID := {A..H}` and ..
* `E := { (ID(a),ID(b)) | (a parent-of b) for (a,b in S) }`

Note that a partial setup has no other requirements that could be used to form
a node tree. That is, the only information available that can be used are the
relationships between the sets in `S`. Consequently, the resulting tree has
one node per set (i.e. `(#N == #S)`) rather than one node per element in `U(S)`
(i.e. `(#N != #U(S))` - 8 nodes, not 5 nodes). Put differently, a setup of `#S`
sets allows to form a node tree of `#S` nodes.

Note that one could enlarge the CSS of each set without changing the amount of
nodes and also without affecting the tree's structure. That is, even if the CSS
of each set would be (e.g.) a 2-element set, the resulting tree would still be
as shown above (i.e. a tree with `#S`) nodes.

Note that, in order to increase the size of `css(s)` one needs to add an
additional characteristic element CE to each set in `A*(s)`.

<!-- ======================================================================= -->
## partial setup =?=> node tree

Even though the relationship a node has with all the other nodes is defined
by those elements that are shared by the sets in `S`, the translation of a
set into a node is independent of these elements. That is, in general a setup
**does not embed the definition of the nodes** themselves.

As shown above, one can still associate a unique id with each set. However,
since the iteration over `S` is random, subsequent runs will yield trees that
have the same structure, but also trees that will in general differ in their
labels (i.e. their id values). Obviously, this randomness is insufficient since
the intention is to reliably recreate a tree from a given input setup.

The issue is therefore how to embed unique object/node identifiers such that
one can reliably determine the identifier that is associated with a particular
set and, based on that, the corresponding object/node. Further requirements
must therefore be introduced such that a setup can be understood to provide
the complete definition of a tree.

Due to the above, one available option is to provide a setup of sets as
**an ordered sequence of sets**. That is because the index-order can then be
understood to provide a unique id for each set - i.e. **an implicit embedding**.
Using this method, one would however be restricted to the use of index-based
identifiers.

Since the elements in `U(S)` have no direct effect on the structure of the
resulting tree, a different option is to require that each element in `U` is a
node identifier. After all, each element in `U` is a **a characteristic element**
and as such unique to the corresponding subset - i.e. **an explicit embedding**.
In contrary to an implicit embedding, and even though one will in general still
use index-based ids, one could choose to use non-numeric ids instead.
