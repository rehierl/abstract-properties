
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

Each relation can be understood to be accompanied by, or to be associated
with a **characteristic function** `R(s)` that allows to determine if a
sequence over the domains is connected in the relation's graph. That is,
`R(s)` returns true for some `s`, iff `G` contains `s` as an element.
Based on that, the elements in sequence `s` can be described as being
**(strictly) connected**.

* `R(s) := (s in G)`
* `chi(×Di), R(×Di) := (×Di) -> boolean`
* where `×Di` is meant to represent `D1,..,DN`

A relation can be described as **finitary**, if it contains a finite amount of
domains. In addition to that, a relation is said to be **binary**, if the
relation has exactly two domains.

A relation can be described as **finite**, if the sum of all cardinalities
over all of its sets is finite. That is, the total number of elements within
its domaints and the number of edges in its graph is finite. A relation can
be described as **infinite**, if either the number of elements in its domains,
or the number of edges in its graph is infinite.

Note that the focus of this discussion is in general on sets of elements each
of which has a limited amount of elements. Because of that, infinite relations
are non-relevant to this discussion.
