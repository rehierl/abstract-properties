
<!-- ======================================================================= -->
# a path-based encoding

Recall that paths, as sequences of vertices, can be formed over the edges of
any relation/graph. With that in mind, any sequence can be understood as the
definition of a graph `G(N,E)` that has one edge for each pair of adjacent
elements in it.

* `s := (s1,s2,...)`
* `N := { s[i] | (i in [1,#s]) }`
* `E := { (s[i],s[i+1]) | (i in [1,#s-1]) }`
* `sem(G) := (a parent-of b)`

Note that `s[i]` defines a parent of `s[i+1]`.

Note that in this kind of encoding, it is the index-order of a sequence that
needs to be understood to define the relationships between the elements in it.

<!-- ======================================================================= -->
## reversing the process of forming paths

Recall that two edges in a graph can be said to form a path, if the sink vertex
of one edge (e.g. `b` in `(a,b)`) is also the source vertex of another edge
(e.g. `(b,c)`). Based on that, paths of vertices can be formed over the edges
of a graph, which can be expressed as sequences of vertices (e.g. `(a,b,c)`).

* `s := (a,b,c)` => is understood to define edges `(a,b)` and `(b,c)`
* `aPc` is understood to be true

The process of forming paths can be understood to be reversible. That is, one
can derive edges from any sequence `s`, by assuming that an edge is defined
for each pair of adjacent vertices. That is, each vertex is a source to an
edge that has the next subsequent vertex as its sink.

* `E := { (s[i],s[i+1]) | (i in [1,#s-1]) }`

Note that the edges defined by a sequence do not differenciate between distinct
**element instances**, each of which can be described as the combination of an
element and its position. That is, each instance of an element is treated as a
reference to the same base element.

<!-- ======================================================================= -->
## the issue with - repeating elements

```
s := (a,a,b,c)
E := { (a,a); (a,b); (b,c) }
============================
a° -> b -> c
```

Difficulties arise as soon as elements appear more than once. However, for as
long as there are no other elements in between the occurrences of the same
element, there isn't much of an issue. That is because such repetitions only
define loops - visualized as (°).

```
s := (a,b,c,b,d)
================
     |<-----|
a -> b -|-> c
        |-> d
```

Since this kind of encoding does not differenciate between element instances,
element (b) is defined to be presequent and also subsequent to itself. Also,
element (c) can be understood to be subsequent and also presequent to (b).

* `(a presequent-to b), (b subsequent-to a) := aPb`

The relationships between the elements are conflicting, if the repetitions of
one element are interleaved by one or more other elements. That is because such
**repetitions add cycles** to the graph of a sequence, which can be understood
to **break the linear order of succession**.

Note that the edges are always oriented from one element towards those elements
that are subsequent to it. Because of that, the only way to define backwards
oriented edges is to repeat one or more elements.

<!-- ======================================================================= -->
## types of partial orders covered

This kind of encoding allows to define symmetric edges (i.e. `(b,c)` and
`(c,b)`), which is in conflict with partial orders. Because of that, the
transitive closure of a graph defined by a sequence that has repeating
elements is **no partial order relation**.

In contrary to that, any ordered sequence can be understood to define
**a total order relation**, which is why **ordered sequences** had to
be defined in order to exclude repeating elements.

* `(E(s) == #s)` is required to be true for ordered sequences
