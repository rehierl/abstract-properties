
<!-- ======================================================================= -->
# normalized setups

A partial/total setup `S` will be referred to as **a normalized setup**,
if the following requirements are met:

* (R3) Each set in `S` must have exactly one CE.
* (R4) Each CE must allow to identify the node a set represents.

Note that no CSS may be empty or have more than one CE.

* `(#css(s) == 1)` must be true for all `(s in S)`
* `U(S)` is effectively treated as a set of nodes/ids

Note that each rooted normalized setup can be understood to define the
structure and the nodes of a node tree.

<!-- ======================================================================= -->
## requirements

Since the relationships between the sets in an input setup `S` translate to
the relationships between the nodes in the resulting tree `T(N,E)`, a setup
must first and foremost be understood to define the structure of a tree.
Desipte that, a setup has no further characteristics that could be relied
upon when creating the nodes of a tree. Additional characteristics are
therefore required:

(1) - `(N subset-of U(S))` - Since it must be possible to determine which node
a set represents, the nodes of the resulting tree must be elements in the setup's
universal set. That is, each node in `T` must be an element of one or more sets
in `S`.

Note that, instead of having actual node objects, one can add unique numeric
identifiers (e.g. the index of a node into an ordered sequence of nodes).

(2) - `(#S >= #N)` - Since the structure of the resulting tree is defined by
the relationships between the sets, distinct sets in `S` represent distinct
nodes in `T`. Each set must therefore contain the node id of the node it
represents, while maintaining the relationships between the sets. Because of
that, one id per set in `S` is required.

(3) - `(node-of: S -> N)` - A method must exist such that the node a set
represents can be reliably identified. That is, the method must be able to
determine the correct node id amongst all other node ids within the any given
set.

<!-- ======================================================================= -->
## one and only one ce per css

(*) Having no CE in a set effectively disallows to determine the node such a
set represents. Each set must therefore have a CE.

(*) Having multiple CEs per set has no other effect than to increase the storage
requirements (hint - `ce(s)` is an element in each set in `rp(s)`). Instead of
having two or more CEs per set it is valid to require that each set has no more
than once CE.

* require `(#css(s) == 1)` to be true

(*) If need be, the CE of a set can be used as an index into an ordered sequence
of nodes. That is, further information can be provided, even if each set has no
more than one CE.

(*) Since each set is now required to have one and only one CE,
one can conclude that `U` is equal to `CE(S)`.

* `(CE(S) == U)` is then true

(*) Since each set is now required to have one and only one CE,
one can conclude that the number of sets in `S` is
equal to the number of elements in `U`.

* `(#S == #U)` is then true

(*) Since each element in `U` is effectively the id of a node,
one can use `U` as the set of nodes `N` for the resulting tree.

* `U(S) => N(T)`

(*) Since each set is now required to have one and only one CE,
the functions to retrieve the CE of a set is defined for each set.

* `node-of(s) := ce(s)` is defined for all `(s in S)`
