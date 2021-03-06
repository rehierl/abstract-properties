
<!-- ======================================================================= -->
# Relationships between graphs

```
(S ? G) -|--> intersects --|--> subgraph-of --|--> proper-subgraph-of
         |                 |                  |
         |--> disjoint-to  |--> overlaps      |--> equal-to
```

The following is a summary of those operators that are similar to those that
are used to describe the relationships between two simple sets.

Note that `disjoint-to` and `subgraph-of` have strict definitions. That is,
a graph either contains all of the vertices and edges of the other (i.e.
subgraph-of), or none at all (i.e. disjoint). In contrary to that, `overlaps`
merely states that one graph must have one or more, but not all of the
corresponding elements of the other. As such, the `overlaps` operator is
unclear (i.e. how many elements exactly?).

Note that the `proper-subgraph-of` operator is the only graph-related operator
that allows to derive an orientation from one graph to the other.

Note that two distinct graphs which do not overlap each other, are either
disjoint ex-or properly related. In the context of simple sets of elements,
this either-or relationship will allow to define partial orders over graphs.

<!-- ======================================================================= -->

* given two graphs `S := (T,U)` and `G := (V,E)`

(S equal-to G)

* `(S == G) := (T == V) and (U == E)`
* i.e. both graphs have equal sets of vertices and equal sets of edges
* i.e. the intersection graph is equal to `S` and equal to `G`
* i.e. `equal-to` has no orientation
* `(S == G) <-> (S subgraph-of G) and (G subgraph-of S)`
* i.e. `S` and `G` are subgraphs to each other

(S unequal-to G)

* `(S != G) := not (S == G)`
* i.e. `unequal-to` is converse to `equal-to`
* synonymous - `distinct-to`, `distinct-from`

(S disjoint-to G)

* `(S disjoint-to G) := (T disjoint-to V)`
* i.e. `S` and `G` have no vertices in common
* i.e. `S` and `G` are disjoint to each other
* i.e. `disjoint-to` has no orientation
* note - `(T disjoint-to V) -> (U disjoint-to E)`

(S intersects G)

* `(S intersects G) := ((T & V) != {})`
* i.e. `S` and `G` have some vertices in common
* i.e. `intersects` is converse to `disjoint-to`
* i.e. `S` and `G` intersect each other
* i.e. `intersects` has no orientation
* note - `(U intersects E) -> (T intersects V)`
* synonymous - `coupled-with` (via some point of contact)

(S subgraph-of G)

* `(S subgraph-of G) := (T subset-of V) and (U subset-of E)`
* i.e. all vertices/edges in `S` are vertices/edges in `G`
* i.e. `subgraph-of` has "some" orientation
* note - `(?? subgraph-of ??)`, `(G subgraph-of G)`

(S contains G)

* `(G contains S) := (S subgraph-of G)`
* note - no issue similar to "element-of" vs. "subset-of"
* synonymous - `subgraph-of`, `inside-of`

(S related-to G)

* `(S related-to G) := (S subset-of G) or (G subset-of S)`
* i.e. one graph is a subgraph of the other
* i.e. `related-to` has no orientation

(S unrelated-to G)

* `(S unrelated-to G) := not (S related-to G)`
* i.e. `unrelated-to` is converse to `related-to`

(S proper-subgraph-of G)

* `(S proper-subgraph-of G) := (S subgraph-of G) and (S != G)`
* i.e. `S` is distinct from, but still a subgraph-of `G`
* `(S proper-subgraph-of G) -> (G proper-supergraph-of S)`
* i.e. `G` has one or more vertices not in `S`
* `(S proper-subgraph-of G) -> (G no-proper-subgraph-of S)`
* i.e. `proper-subgraph-of` is strictly oriented
* synonymous - `strict-subgraph-of`

(S properly-related-to G)

* `(S properly-related-to G) := (S related-to G) and (S != G)`
* i.e. `S` is distinct from, but still related to `G`
* i.e. both are unequal and one is a subgraph of the other
* i.e. `properly-related-to` has no orientation
* synonymous - `strictly-related-to`

(S overlaps G)

* `(S overlaps G) := (S intersects G) and (S unrelated-to G)`
* i.e. each graph has a vertex not in the other
* i.e. `overlaps` has no orientation
