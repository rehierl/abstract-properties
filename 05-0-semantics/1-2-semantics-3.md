
<!-- ======================================================================= -->
## TODO

The open question is, what effects an inconsistent mapping would have? If the
mapping is consistent, then an edge can be understood to correspond with its
semantical expression. Put differently, an edge itself would represent its
own expression.

A binary operation, used to represent a semantical expression, has a 1st and
a 2nd operand. The oder of operands can therefore be mapped onto the order of
arguments. Note however, that it is the operator that defines the relationship
between both of its operands and based on that the semantics of an expression;
not the order of operands (e.g. "(x child-of y)" vs. "(x parent-of y)").

<!-- ======================================================================= -->

An **index-to-argument mapping** can be defined
based on the index of each component in an edge.

* `sem(f) := (f[1] multiple-of f[2])` for edge `(f in E)`
* `sem(g) := (g[2] multiple-of g[1])` for edge `(g in E)`

Note that each component is in general implicitly dereferenced to the element
it holds. In that case, `f[1]` needs to be read as representing the tuple's
first vertex rather than its first component.

Note that both of these expressions are distinct (i.e. `(sem(f) != sem(g))`)
since the vertex-to-argument mappings in both are distinct. Other than that,
both expressions are equal since they both have an argument which is a multiple
of the other (role-1) and an argument which divides the other without remainder
(role-2). That is, both expressions have the same set of semantical roles.

<!-- ======================================================================= -->
## consistently oriented semantics

Because each edge `e := (x,y)` in a graph is defined as a tuple of two vertices,
each edge has a 1st and a 2nd vertex. As such, each edge is understood to be
directed from its 1st vertex `x` to its 2nd vertex `y` (i.e. `(x -> y)`).
Because of that, a graph may be understood as having **directed/oriented edges**.

* `dir(e) := (x -> y)` for `e := (x,y)` and `(e in E)`
* i.e. edge `e` begins in `x` and ends in `y`

Note that edges, by definition, begin in their first and end in their second
component. This basic orientation can not be changed (to for example begin in
its second and end in its first component). Despite that, the association of
the components in an edge with the vertex they hold is still variable when
defining a graph.

Similar to the orientation of an edge, the semantics of an edge may provide
its own sense of orientation (i.e. **oriented semantics**), if the vertices
are considered to be unequal. Conversely, both vertices may count as being
equal (i.e. un-oriented semantics). (Note that the edges in a directed graph
are all expected to have oriented semantics. That is because otherwise, an
undirected graph would be more appropriate).

Note that the semantics of edges `f` and `g` have opposite orientation. That
is, the orientation of `sem(f)` corresponds with the orientation of edge `f`.
In contrary to that, `sem(g)` is oriented against edge `g`.

* `dir(sem(f)) := (x -> y)`, if `(f := (x,y))`
* `dir(sem(g)) := (x <- y)`, if `(g := (x,y))`

Because of that, edge `e` is said to have **consistently oriented semantics**,
if the orientation of `sem(e)` corresponds with the orientation of that edge
(e.g. `sem(f)`). Conversely, edge `e` is said to have **inconsistently oriented
semantics**, if that is not the case (e.g. `sem(g)`).

Likewise, the set of edges `E` is said to have consistently oriented semantics,
if all of its edges are consistently oriented. (Note that `E` may even be a
heterogenous set of edges). Conversely, `E` is said to have inconsistently
oriented semantics, if that is not the case.

Similar to that, a graph `G` is said to have consistently oriented semantics,
if its homogenous set of edges is consistently oriented. (Note that `G` must
have a homogenous set of edges). Conversely, `G` is said to have inconsistently
oriented semantics, if that is not the case.

Note that a graph with mixed semantics can not be said to have consistently
oriented semantics since the semantics of such a graph is from a strict point
of view undefined. If applicable, one could still refer to its set of edges
as being "a heterogenous set of edges with consistently (or inconsistently)
oriented semantics".

<!-- ======================================================================= -->
## remarks

Note that in the context of this discussion, a graph is in general expected
to have a consistently oriented homogenous set of edges. That is, a graph is
itself expected to be accompanied by a single consistently oriented semantical
expression that applies to all of its edges.

Note that two distinct graphs `G` and `H`, which are based upon the same sort
of vertices (i.e. the same sort of objects they represent), and which have the
same semantics, may be referred to as being **graphs of the same sort** (i.e.
`(V(G) ~ V(H))` and `(sem(G) == sem(H))`, where `~` is understood to compare
the types of both vertex sets).

Note that, if an operation is defined for two graph arguments, then both of its
operands are implicitly expected to be graphs of the same sort. Because of that,
operations may only be applicable after the execution of semantical conversions.
