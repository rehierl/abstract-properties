
<!-- ======================================================================= -->
## the semantics of an edge (e/E/G)

A graph `G := (V,E)` represents the relationships between its vertices. Because
of that, an expression must exist for each edge which explains why both of its
endpoints are adjacent to each other. Such an expression will be referred to
as the **semantics of an edge**.

* `sem(e) := (x multiple-of y)` for an edge `((x,y) in E)`

Note that the semantics of two distinct edges `e1` and `e2` in a graph are not
required to be identical. That is, the semantics of two edges in the same graph
may in general be distinct for whatever reason.

* `sem(e1) := (x multiple-of y)` for `e1 := (x,y)`
* `sem(e2) := (u divisible-by v)` for `e2 := (u,v)`

Because of that, a graph can be understood to be accompanied by a set of
tuples that defines the mapping between the edges and their semantics,
which may be referred to as the **edge-to-semantics mapping** of a graph.

* `G := (V,E,S)` where `S` could be defined as ...
* `S := { (e,s) | (e in E) and (s == sem(e)) }`

Based on that, `sem()` could be defined as ...

* `(sem: E -> Expression)`, where `(sem(e) == s)` if `((e,s) in S)`
* i.e. `sem(e)` returns the semantical expression of edge `e`

If the expression of an edge is seen as the "type" of an edge, then a graph
can be referred to as having a **homogenous set of edges**, if the semantics
of each edge is identical to the semantics of all the other edges. Conversely,
a graph may be referred to as having a **heterogenous set of edges**, if that
is not the case. Put differently, a homogenous set of edges can be understood
to hold **edges of the same sort**.

* `homogenous(E) := (sem(e) == sem(f))` for any pair of edges `(e,f in E)`
* `heterogenous(E) := not homogenous(E)`

In the context of this discussion, all graphs are assumed to have homogenous
sets of edges. Because of that, the **semantics of a graph** `sem(G)` can be
defined by the semantics of its edges `sem(e)` (i.e. `(sem(e) => sem(G)`).
Put differently, the semantics of a graph can also be understood to define
the semantics of its edges (i.e. `(sem(G) => sem(e))`).

* `homogenous(G) := (sem(G) <-> sem(e))` for each edge `(e in E)`
* i.e. `homogenous(G) -> homogenous(E)`
* `heterogenous(G) := not homogenous(G)`

Note that the semantics of a graph, that has a heterogenous set of edges,
is strictly speaking undefined since it is not associated with one dedicated
expression. Because of that, one could speak of a graph as having ...

* **uniform semantics** (if `G` is homogenous) or
* **mixed semantics** (if `G` is heterogenous)

Note that the null graph and a graph with a single edge may be described as
having uniform semantics since there is no pair of edges that could be in
conflict with the above definitions.

Note that on a formal level, a graph that has mixed semantics could have
semantics that do not correspond with the semantics of even one edge. Such
a case however needs to be seen from a purely theoretical point of view.

<!-- ======================================================================= -->
## index-based semantics

Each endpoint in an edge has a specific role in the expression of an edge. Some
means is therefore required which allows to map an endpoint to its **semantical
role**. Put differently, a method is required which allows to map the vertices
of an edge `e` to the arguments in its semantical expression/statement `s`.

* `e := (v1,v2)` and `sem(e) := s` where `s := (x multiple-of y)`

The issue is that an edge, as a tuple of elements, does by itself not allow to
identify which vertex maps to argument `x` and which to argument `y`. However,
a non-empty tuple is accompanied by a bijective **index-to-component mapping**
since by definition it always has a first and a last component. (Note that all
components in a tuple may hold the same element. The focus therefore is on
components rather than on elements).

* `t := (c1,c2)` => `(t: Index -> Component)` => `t := { (1,c1), (2,c2) }`

Since an edge begins by definition in its 1st/source vertex and ends in its
2nd/sink vertex, the (structural) **index-to-endpoint mapping** of an edge is
fixed. (Note that in a loop/reflexive edge, the vertex it holds maps to both
endpoints. In contrary to that, the index of a vertex is unique to it, if an
edge has two distinct vertices as its endpoints).

* `e := (v1,v2) => (e: v1 -> v2)`

Since each semantical expression has one or more semantical arguments, each of
which represents a distinct semantical role, each expression can be thought of
as being reduced to an ordered list of distinct arguments:

* `s := (a1,a2)` => `(s: Index -> Argument)` => `s := { (1,a1), (2,a2) }`
* e.g. `s := (x multiple-of y)` => `s := (x,y)`

At this point, the order of arguments (i.e. "first" vs. "last") in an
expression needs to be understood as being arbitrarily selected (e.g. in order
of appearance). That is, there is no definition as to which argument has to be
the first or the last. For such a definition to exist, one would have to require
that both arguments have certain characteristics which allow to choose one over
the other (e.g. superordinate-to, more-significant-than). Because of that, the
(semantical) **index-to-argument mapping** of an expression is unspecified.

* `vertex <?=> e[i] <=?=> s[j] <=> argument`

Note that the 1st/source vertex of an edge does not necessarily have to be
mapped to the 1st arguments in its semantical expression. Likewise, the 1st
semantical argument of an edge does not necessarily have to be mapped to
its source vertex. Put differently, the index-to-endpoint mapping does not
necessarily have to correspond with the index-to-argument mapping.

* `(v1,v2) <-> (a1,a2)` or `(v1,v2) <-> (a2,a1)`?
* `(a1,a2) <-> (v1,v2)` or `(a1,a2) <-> (v2,v1)`?

From the 2nd perspective, the order of arguments defines which argument
will be mapped to the source and which to the sink of an edge.
