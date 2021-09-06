
<!-- ======================================================================= -->
# normalized setups

A partial/total setup `S` can be described as **a normalized setup**,
if the following requirements are met:

* (R1) Each set in `S` has exactly one CE.
* (R2) Each CE must be a unique node identifier of some sort.

Due to R1 no CSS may be empty or have more than one CE.

* `(#css(s) == 1)` must be true for all `(s in S)`
* `U(S)` is effectively a set of node identifiers

<!-- ======================================================================= -->
## requirements

Since the relationships between the sets in an input setup `S` define the
relationships between the nodes in the resulting tree `T(N,E)`, a setup must
first and foremost be understood to define the structure of a tree. Desipte
that, a setup has no further characteristics that could be relied upon when
creating the nodes of a tree. Additional characteristics are therefore
required:

(1) - `(N subset-of U(S))` - Since it must be possible to determine which node
a set represents, the node ids of the resulting tree must be elements in the
setup's universal set. That is, each node id in `N(T)` must be an element of
one or more sets in `S`.

(2) - `(#S == #N)` - Since the structure of the resulting tree is defined by
the relationships between the sets, distinct sets in `S` represent distinct
nodes in `T`. Each set must therefore contain the node id of the node it
represents, while maintaining the relationships between the sets. Because
of that, one id per set in `S` must be required.

Recall the conclusions drawn in the chapter on characteristic subsets.
Due to the above, `(#U == #S)` and `(N == S)` are both consequences of (2).

(3) - `(node-of: S -> N)` - A method must exist such that the node a set
represents can be reliably identified. That is, the method must be able to
determine the correct node id amongst all other node ids within the any given
set.

<!-- ======================================================================= -->
## one and only one ce per css

(*) Having no CE in set `s` effectively disallows to determine the node
set `s` represents. Each set must therefore have a CE.

(*) Having multiple CEs per set has no other effect than to increase the
storage requirements (hint - `ce(s)` is an element in each set in `rp(s)`).
Instead of having two or more CEs per set it is valid to require that each
set has no more than once CE.

* require `(#css(s) == 1)` to be true

(*) It seems reasonable to require that the CE of a set can be used as an
index into an ordered sequence of nodes. That is, further information can
be provided, even if each set has no more than one CE.

(*) Since each set is now required to have one and only one CE, one can
conclude that `U` is equal to `CE(S)` and as such a set of node identifiers.

* `(CE(S) == U)` is then true

(*) One can then conclude that the number of sets in `S` is equal to the
number of elements in `U`.

* `(#S == #U)` is then true

(*) One can then use `U` as the set of nodes `N` for the resulting tree.

* `U(S) => N(T)`

(*) Since each set is now required to have one and only one CE,
the functions to retrieve the CE of a set is defined for each set.

* `node-of(s) := ce(s)` is defined for all `(s in S)`