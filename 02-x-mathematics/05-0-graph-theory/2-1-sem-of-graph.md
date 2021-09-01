
<!-- ======================================================================= -->
## the semantics of a graph

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

Because of that, a graph can be understood to be accompanied by a set of tuples
that defines the mapping between the edges and their semantics, which may be
referred to as the **edge-to-semantics mapping** of a graph.

* `G := (V,E,S)` where `S` could be defined as ...
* `S := { (e,s) | (e in E) and (s == sem(e)) }`

Based on that, `sem()` could be defined as ...

* `(sem: E -> Expression)`, where `(sem(e) == s)` if `((e,s) in S)`
* i.e. `sem(e)` returns the semantical expression of edge `e`

Due to the above, a graph can be thought of as being accompanied by a set of
expressions `SEM()` which contains all the expressions that are associated
with at least one of its edges.

* `(SEM: {G} -> {Expression})`
* `SEM(G) := { sem(e) | (e in E(G)) }`

If the expression of an edge is seen as the "type" of an edge, then a graph
can be referred to as having a **homogenous set of edges**, if the semantics
of each edge is identical to the semantics of all the other edges. Conversely,
a graph may be referred to as having a **heterogenous set of edges**, if that
is not the case. Put differently, a homogenous set of edges can be understood
to hold **edges of the same sort/kind**.

* `homogenous(E) := (sem(e) == sem(f))` for any pair of edges `(e,f in E)`
* `heterogenous(E) := not homogenous(E)`

In the context of this discussion, all graphs are assumed to have homogenous
sets of edges. Because of that, the **semantics of a graph** `sem(G)` can be
defined by the semantics of its edges `sem(e)` (i.e. `(sem(e) => sem(G)`).
Conversely, the semantics of a graph can be understood to define the semantics
of its edges (i.e. `(sem(G) => sem(e))`).

* `homogenous(G) := (#SEM(G) <= 1)`
* `heterogenous(G) := (#SEM(G) > 1)`

Note that the semantics of a graph, that has a heterogenous set of edges,
is strictly speaking undefined since it is not associated with one specific
expression. Because of that, one could speak of a graph as having ...

* **uniform semantics** if `G` is homogenous
* **mixed semantics** if `G` is heterogenous

Note that the semantics of a graph `G` is first and foremost of **descriptive**
nature. That is, its semantics is used to describe its edges and is as such,
unlike with the semantics of an order relation `R`, not the primary reason for
the existence of its edges.

* `aGb -> (a presequent-to b)`
* `aRb <-> (a presequent-to b)`

Note that the null graph and a graph with a single edge may be described as
having uniform semantics since there is no pair of edges that could be in
conflict with these definitions.
