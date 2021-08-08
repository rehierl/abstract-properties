
<!-- ======================================================================= -->
## converse, transpose (°)

The standard definition of a converse graph `G°` is defined as follows:

* `G° := (V,E°)` such that `E° := { (b,a) | aEb }`
* i.e. the order of vertices in each edge is turned upside-down

Based on that, an operation can be defined which returns the
converse graph `G°` of a graph `G`:

* `(G°: Graph -> Graph)`, where `G°(G)` returns the converse `G°` of `G`
* `conv(G), := G°(G)` where `conv(conv(G)) <-> G`

Note that this definition does not state anything about the semantics of the
converse graph. That is, this operation only focuses on "flipping" the edges.
Because of that, and from a strict perspective, the semantics of the converse
graph `G°` must be understood to be undefined because the initial semantics
can no longer apply (since the endpoints of an edge have distinct roles).

<!-- ======================================================================= -->
## converse semantics

Assumed that the semantics of a graph `sem(G)` is defined as `(p parent-of c)`,
such that each edge is a tuple in the following order `(e := (p,c))`, then the
semantics of its edges is defined as `sem(e) := (e[1] parent-of e[2])`.

* `((p,c) in G)` => `(e[1] parent-of e[2])` => `(p parent-of c)`
* note - `sem(e)` is oriented in the direction of `dir(e)`

If such a graph would have to be conversed according to the above definition,
then, without any further change, the graph's initial semantics could not
apply to its converse:

* `((c,p) in G°)` => `(e[1] parent-of e[2])` => `(c parent-of p)` => error
* note - semantics have an implicit, index-based vertex-to-argument mapping

Obviously, the converse operation also needs to adjust the semantics of the
initial graph `G`. That is because the order of arguments in the semantical
expression `sem(G)` is otherwise broken in `G°`.

* `((c,p) in G°)` => `(e[2] parent-of e[1])` => `(p parent-of c)` (ok)
* note - `sem(e)` is now oriented against `dir(e)` (not quite ok)

Even though the new expression now applies to the flipped edges, the edges end
up having inconsistently oriented semantics. In a context where the semantics
of a graph are of no importance, such an adjustment might seem to be sufficient.
However, if the orientation of the semantics of a graph are relevant, then that
aspect needs to be fixed as well.

In order to fix both of the above aspects, one needs to replace the semantics
of an initial graph with semantics that has the opposite meaning. That is, the
semantics of the initial graph needs to be replaced by its relational antonym
(aka. **converse semantics**, antonymous semantics).

* `((c,p) in G°)` => `(e[1] child-of e[2])` => `(c child-of p)` (ok)
* `parent-of` => `child-of`

**Memory hook**
A converse/antonymous graph needs converse/antonymous semantics.

<!-- ======================================================================= -->
## remarks

The following is a short list of pairs of converse semantics:

* super-ordinate-to <=> sub-ordinate-to
* more-significant-than <=> less-significant-than
* contains (as an element) <=> element-of

The following is a list of pairs of more specific semantics:

* parent-of <=> child-of
* superset-of <=> subset-of
* subsequent-to <=> presequent-to

Note that, if the converse of a graph needs to be created in the context
of this discussion, then a converse graph is also expected to have converse
semantics. That is, in the context of this discussion, a converse graph
has flipped edges *and* converse semantics.
