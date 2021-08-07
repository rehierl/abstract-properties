
<!-- ======================================================================= -->
# graph theory

A graph `G := (V,E)` is defined as an endo-relation that consists of a set of
**vertices** `V` and a set of **edges** `E`. As such, and like an ordered set,
a graph is a complex value/type.

* `G := (V,E)` such that `(E subset-of (V × V))`

Note that a graph can be described as being **undirected**, if its set of edges
(aka. a set of arcs `A`) consists of 2-element sets. As such, a graph may also
be described as **a simple graph**. If, in contrary to that, a graph's set of
edges consists of 2-element tuples/sequences, then the graph can be described
as being **directed** and can therefore be described as **a digraph**.

Note that the focus of Graph Theory is in general on undirected loop-less
graphs. In contrary to that, the focus of this discussion is on directed
graphs (i.e. digraphs), that are in general required to have the following
default characteristics:

* a non-empty homogenous sets of vertices
* a non-empty set of directed edges
* finitely many vertices and edges
* a loop-less and acyclic graph

Note that, in contrary to the order relation of an ordered set, the relation
of a graph is in general neither reflexive nor transitive.

* `aEa` is in general be false for all vertices
* `aEc` is not required to exist, even if `aEb` and `bEc` both exist

<!-- ======================================================================= -->
## objects vs. vertices

A graph is defined to represent the connections between its elements. These
elements are taken from its set of vertices `V`. Each vertex `(v in V)` can
be understood to represent an object of some kind, each of which that can be
considered an element of some overall set of Objects `O`. As such, the vertices
in a graph represent abstract units whose object properties are in general
considered to be non-relevant to a graph.

Note that, a vertex may in general represent any object. That is, two distinct
vertices may represent entirely different objects or even the exact same object.
However, in the context of this discussion, it is assumed that two distinct
vertices always represent distinct objects.

Based on that, one can assume that a bijective function `(o: V -> O)` exists
which allows to lookup the object of any given vertex. Since `o()` is required
to be bijective, an inverse `(v: O -> V)` can be assumed to exist which allows
to lookup the vertex of any given object. Because of that, each vertex can
be understood as a numerical identifier.

* `o(v)` returns the object `o` vertex `v` represents
* `(a != b) <=> (o(a) != o(b))` for some `(a,b in V)`
* `v(o)` returns the id/reference/vertex of object `o`
* `v()` is inverse to `o()`
