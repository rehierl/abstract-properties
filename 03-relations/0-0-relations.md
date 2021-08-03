
<!-- ======================================================================= -->
# relations

A relation `R` is a sequence of one or more sets of elements of length `N+1`.
The first `N` sets are used to denote sets of abstract values (aka. **domains**
or **sets of vertices**). In contrary to that, the last set (aka. **graph**)
can be understood to define connections over the elements within the domains.

* `R := (D1,..,DN,G)` where `(N in [1,*])`
* and `(G subset-of (D1 × .. × DN))`

Note that the graph `G` of relation `R` is understood to consist of flat
sequences of elements (i.e. not the strict cartesian product). And since
these sequences of elements are no sets of elements, all the sequences in
`G` can be understood to be **directed**. Based on that, any relation can
be described as being directed.

Note that a relation can itself be seen as an abstract value. That however is
not the focus of this discussion since the intention is not to use multiple
relations as the (e.g.) elements of a simple set. In the context of this
discussion, mathematical relations will be **treated as an abstract concept**.
That is, a relation needs to be seen as the formal description of a "thing".

Each relation can be understood to be accompanied by (or associated with)
a **characteristic function** `R(s)` which allows to determine if a given
sequence over the domains is connected in the relation's graph. That is,
`R(s)` returns true for some `s`, iff `G` contains `s` as an element.
Based on that, the elements in sequence `s` can be described as being
**(strictly) connected**.

* `R(s) := (s in G)`
* `chi(×Di), R(×Di) := (×Di) -> boolean`
* where `×Di` is meant to represent `D1,..,DN`

A relation can be described as **finitary**, if it contains a finite amount
of domains. In addition to that, a relation is said to be **binary**, if the
relation has exactly two domains.

<!-- ======================================================================= -->
## endo-relations

A relation that can be described as binary and homogenous (i.e. both domains
are the same), is in general referred to as an **endo-relation**.

* `R := (D,D,G)` where `(G subset-of P(D×D))`

All the sequences in `G` are 2-element sequences and will therefore be referred
to as (directed) **edges**. As such, the vertices of an edge will be referred
to as its **endpoints** with the 1st endpoint being the **source** and the 2nd
endpoint as being the **sink** vertext. Based on that, an edge can be understood
to lead from its source vertex to its sink vertex.

In addition to the above, the following syntactic "shortcuts" will be used:

* `R := (D,G) := (D,D,G)`
* `(s in R) := (s in G)`
* `aRb := ((a,b) in G)`
* `!aRb := ((a,b) not in G)`

Note that, as with any other relation, each of the vertices in all of the
sequences in `G` are required to be elements within the corresponding domain.
However, not every element within a domain is also required to be an endpoint
in such a sequence. Such a vertex can be described as being **disconnected**,
or as being **unrelated** (to another vertex).

Note that, since the overall focus in the context of this discussion is on
"related things", disconnected vertices will be **silently ignored**. Based
on that, the domain of a mathematical relation can be understood as a mere
consequence of the corresponding set of edges. After all, a domain is still
required to contain both of the endpoints of each edge.

Note that, based on the focus of the edges in an endo-relation, a relation
can in essence be thought of as being reduced to its set of edges. Based on
that, operations over relations can be defined similar to those over simple
sets of elements.
