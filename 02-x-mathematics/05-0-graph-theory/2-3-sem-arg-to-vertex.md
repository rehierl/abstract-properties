
<!-- ======================================================================= -->
## index-based semantical mapping

Each endpoint in an edge has a specific role in the semantical expression of an
edge. Some means are therefore required which allow to map an endpoint to its
**semantical role**. Put differently, a method is required which allows to map
the vertices of an edge `e` to the **semantical arguments** in an expression `s`.

* `e := (v1,v2)` and `sem(e) := s` where `s := (x multiple-of y)`
* `dir(e) := (v1 -> v2)` and `dir(s) := (x -> y)`

<!-- ======================================================================= -->
## argument-to-vertex mapping

The issue is that an edge, as a 2-element sequence of elements, does by itself
not allow to identify which vertex maps to argument `x` and which to argument
`y`. However, each non-empty sequence is always accompanied by an **index order**
over its components.

Note that all components in a sequence may hold the same element. The focus is
therefore is on components, rather than on elements. Or, from a different point
of view, the focus is on edges that connect distinct vertices.

* `s := (c1,c2)` => `(s: Index -> Component)` => `s := { (1,c1), (2,c2) }`

Since an edge begins by definition in its 1st/source vertex and ends in its
2nd/sink vertex, the (structural) **index-to-endpoint mapping** of an edge is
fixed.

* `e := (v1,v2) => (e: v1 -> v2)`

Since each semantical expression has one or more semantical arguments, each of
which represents a distinct semantical role, each expression can be thought of
as being reduced to an ordered sequence of arguments:

* `s := (a1,a2)` => `(s: Index -> Argument)` => `s := { (1,a1), (2,a2) }`
* e.g. `s := (a1 multiple-of a2)` => `s := (a1,a2)`

At this point, the order of arguments (i.e. "first" vs. "last") in an expression
must be understood as being arbitrarily selected (e.g. in order of appearance).
That is, there is no definition as to which argument has to be the first or the
last.

For such a definition to exist, one would have to require that both arguments
have certain characteristics which allow to choose one over the other (e.g.
superordinate-to, more-significant-than). Because of that, the (semantical)
**index-to-argument mapping** of an expression is unspecified.

* `vertex <=> e[i] <=> s[j] <=> argument`

Note that the 1st/source vertex of an edge does not necessarily have to be
mapped to the 1st argument in its semantical expression. Likewise, the 1st
semantical argument of an expression does not necessarily have to be mapped to
the 2nd/sink vertex of an edge. Put differently, the index-to-vertex mapping
does not have to be **consistent** with the index-to-argument mapping.

* `(v1,v2) <-> (a1,a2)` or `(v1,v2) <-> (a2,a1)`

<!-- ======================================================================= -->
## consistently oriented semantics?

A binary operation, used to represent a semantical expression, has a 1st and
a 2nd operand. The oder of operands can therefore be mapped onto the order of
arguments.

Note however, that it is the operator that defines the relationship between
its operands and based on that the semantics of an expression; not the order
of operands (e.g. "(x child-of y)" vs. "(x parent-of y)").

If the above argument-to-vertex mapping is consistent, then an edge can be
understood to correspond with its semantical expression. Put differently,
an edge itself would essentially represent its own expression.

* `sem(f) := (f[1] multiple-of f[2])` for edge `(f in E)`
* `sem(g) := (g[2] multiple-of g[1])` for edge `(g in E)`

Note that `sem(g)` can be understood to result from forming a converse graph.
That is because each edge in a coverse graph is turned upside-down.

Note that both of these expressions are distinct (i.e. `(sem(f) != sem(g))`)
since the argument-to-vertex mappings in both are distinct. Other than that,
both expressions are equal since they both have an argument which is a multiple
of the other (role-1) and an argument which divides the other without remainder
(role-2). That is, both expressions have the same set of semantical roles.

<!-- ======================================================================= -->
## consistently oriented semantics

Similar to the orientation of an edge, the semantics of an edge may provide
its own sense of orientation (i.e. **oriented semantics**), if the arguments
are considered to be unequal. Conversely, both arguments may count as being
equal (i.e. un-oriented semantics).

Based on that, an edge `e` is said to have **consistently oriented semantics**,
if the orientation of `sem(e)` corresponds with the orientation of that edge.
Conversely, edge `e` is said to have inconsistently oriented semantics, if that
is not the case (e.g. `sem(g)`).

Note that, as a general rule of thumb, semantics can be considered consistent,
if they allow to read an edge "as is". That is, if the vertex order of an edge
matches the argument order of its semantical expression.

Note that, as an example of inconsistently oriented semantics, one can think
of a downward-oriented tree of nodes - i.e. an arborescence. That is, the edges
are oriented from a parent node to a child node. The `child-of` semantics can
be considered inconsistent with that structural orientation

* `e := (a,b) => (a parent-of b)`
* `sem(e) := (b child-of a)` => inconsistently oriented
* `sem(e) := (a parent-of b)` => consistent orientation

Likewise, the set of edges `E` is said to have consistently oriented semantics,
if all of its edges are consistently oriented. (Note that `E` may even be a
heterogenous set of edges). Conversely, `E` is said to have inconsistently
oriented semantics, if that is not the case.

Similar to that, a graph `G` is said to have consistently oriented semantics,
if its homogenous set of edges is consistently oriented. (Note that `G` must
have a homogenous set of edges). Conversely, `G` is said to have inconsistently
oriented semantics, if that is not the case.

Note that a graph with mixed semantics can not be said to have consistently
oriented semantics since the semantics of such a graph is, from a strict point
of view, undefined. If applicable, one could still refer to its set of edges
as being "a heterogenous set of edges with consistently (or inconsistently)
oriented semantics".

<!-- ======================================================================= -->
## default (generic) semantics

As with any other endo-relation, one can associate semantics with the edges
and the paths over a graph that are independent of specific semantical roles.

* `sem(aEb) := (a predecessor-of b)`
* `sem(aEb) := (b successor-of a)`

path-based semantics

* `sem(aPb) := (a presequent-to b)`
* `sem(aPb) := (b subsequent-to a)`

Note that one can define a mapping between these generic semantics
and more specific ones.

* e.g. `(a parent-of b) := (a predecessor-of b)`

<!-- ======================================================================= -->
## general remarks

Note that in the context of this discussion, a graph is in general expected
to have a consistently oriented homogenous set of edges. That is, a graph is
itself expected to be accompanied by a single consistently oriented semantical
expression that applies to all of its edges.

Note that two distinct graphs `G` and `H`, which are based upon the same sort
of vertices (i.e. the same sort of objects they represent), and which have the
same semantics, may be referred to as being **graphs of the same sort** (i.e.
`(V(G) ~ V(H))` and `(sem(G) == sem(H))`, where `~` is understood to compare
the types of both vertex sets).
