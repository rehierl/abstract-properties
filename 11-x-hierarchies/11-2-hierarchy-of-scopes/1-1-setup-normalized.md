
<!-- ======================================================================= -->
# normalized setups

A partial setup `S` can be described as **a normalized setup**,
if the following requirements are met.

* (R0) `S` is a partial setup of sets.
* (R1) Each set `(s in S)` has one and only one CE.
* (R2) Each CE can be treated as a node identifier.

Based on requirement R1, no CSS may be empty or have more than one CE.

* `(#css(s) == 1)` must be true for all `(s in S)`
* `U(S)` is a set of node identifiers

Note that each setup can be understood to be accompanied by a mapping which
allows to translate the node references embedded as characteristic elements
into the corresponding node definitions. Such a mapping may be an ordered
sequence of node definitions, if the CE in each set is the index of the
corresponding definition in the ordered sequence.

<!-- ======================================================================= -->
## a visual simplification

```
|-1-----------| |-4-----|
| |-2-| |-3-| | | |-5-| |
| |---| |---| | | |---| |
|-------------| |-------|
```

Note that, since each set is required to have one and only one CE, one may
denote the CE of each set by treating it as a label of the corresponding set
in the visualization of such a setup. As can be seen, this allows to reduce
the height of such a visualization - i.e. a visual simplification. However,
since each leaf set then has only that CE as an element, one must keep in
mind that the label is, as a CE, still an element in that set.

<!-- ======================================================================= -->
## requirements

Since the relationships between the sets in an input setup `S` define the
relationships between the nodes in the resulting tree `T(N,E)`, a setup must
first and foremost be understood to define the structure of a tree. Despite
that, a setup has no further characteristics that could be relied upon when
creating the nodes of a tree. Additional characteristics are thus required.

(1) - `(N(T) subset-of U(S))` - Since it must be possible to determine which
node a set represents, the node identifiers of the resulting tree must be
elements in the setup's universal set. That is, each node id in `N(T)` must
be an element of one or more sets in `S`.

(2) - `(#S == #N)` - Since the structure of the resulting tree is defined by
the relationships between the sets, distinct sets in `S` represent distinct
nodes in `T`. Each set must therefore contain the node identifier of the node
that set represents, while maintaining the relationships between the sets.
Because of that, one unique identifier per set in `S` is required.

Based on the conclusions drawn in the chapter on characteristic subsets, and
due to the above, `(#U == #S)` and `(N == U(S))` are both consequences of (2).

(3) - `(node-of: S -> N)` - A method must exist such that the node a set
represents can be uniquely identified. That is, the method must allow to
determine the correct node id amongst all other node ids in any given set.

<!-- ======================================================================= -->
## one and only one ce per css

(*) Having no CE in a set effectively disallows to determine the node that
particular set represents. Each set must therefore have a CE.

(*) Having multiple CEs per set has the effect of increasing the storage
requirements (hint - a CE is an element in each set in `A(s)`). Instead of
having two or more CEs per set, it is sufficient to require that each set
has no more than one CE.

* `(#css(s) == 1)` is required to be true

(*) It seems reasonable to require that the CE of a set can be used as an
index into an ordered sequence of nodes. Further information can then be
provided, even if each set has no more than one CE.

(*) Since each set is required to have one and only one CE, one can conclude
that `U(S)` is equal to `CE(S)` and as such a pure set of node identifiers.

* `(CE(S) == U(S))` is true

(*) One can now conclude that the number of sets in `S` is equal to the
number of elements in `U(S)`.

* `(#S == #U)` is true

(*) One can then use `U(S)` as the set of nodes `N` of the resulting tree.

* `U(S) => N(T)`

(*) Since each set is now required to have one and only one CE, a method does
exist that allows to retrieve the CE of a set. Furthermore, this function is
defined for each set in the source setup.

* `node-of(s) := ce(s)` is defined for all `(s in S)`
