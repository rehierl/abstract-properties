
<!-- ======================================================================= -->
# sets of base orders

A processing order and its trivial suborder both represent viable base orders.
Because of that, any processing order allows to define **a set of base orders**
such that any scope over that processing order is in regards to one of the base
orders it contains.

Note that, in the context of this discussion, such a system of base orders will
be referred to as **a type system (of scopes)**. That is, the base orders in
such a set are understood to define certain **types of scopes**.

Depending on the requirements of a particular context, such a type system may
or may not include the trivial base order. Likewise, it may or may not include
the processing order. And finally, a type system may or may not include other
base orders in addition to the afore mentioned. That is, even though a type
system can be expected to have at least one base order, a type system can not
be required to include any base order in particular.

* **expected to be non-empty**
* may include the trival suborder
* may include the processing order
* may include other base orders

Note that a type system can be understood such that it defines the kinds of
scopes that are allowed in a given context. A type system will in general
contain all the base orders that can be supported.

<!-- ======================================================================= -->
## an order of base orders

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

* DTR - the (TR)ivial (D)ocument order
* DTU - the (U)nordered (D)ocument (T)ree
* DTO - the (O)rdered (D)ocument (T)ree
* DPR - the (PR)e-order tree traversal

Recall that the processing order (DPR) is **a linear extension** to the ordered
doctree (DTO), the unordered doctree (DTU) and consequently also to the trival
sub-order (DTR). And like any super-order, the processing order is order
preserving to all of these suborders.

Note that a partial/linear extension is defined as the process of refining some
source order. In contrary to that, the above use of "linear extension" refers
to the result of such a process. This usage must therefore be understood to
implicitly refer to the combination of extensions which allow to transition
from the source order to the resulting order. That is, a combined process is
or can be expected to exist.

```
DPR --> DTO --> DTU --> DTR
|< minimal       maximal >|
```

Recall that the order relation of a processing order is total and therefore
transitive. With that in mind, an extension process can be understood such that
**a subset of edges** of the total order relation is added to a pre-existing
order relation. A transitive closure is then performed on the result in order
to form the final order relation, which may be an intermediate order relation
(i.e. not necessarily the processing order).

Due to the above, one can define an order `P(V,<)` over a set of node orders
`V` such that it is based on a containment order over the sets of edges `E()`
in each order relation.

* `P(V,<)` such that each `(v in V)` is a base order
* `(a < b) := (E(a) superset-of E(b))`

Since the focus of this discussion is on the processing order of a document
tree, order `P` has the processing order DPR (i.e. the pre-order node order)
as its root order.

Note that the order visualized above (i.e. "DPR to DTR") is complete and total.
That is, it effectively descripes a step-wise extension from the trival order
DTR to the prodessing order DPR. Such a system may in general be described as
**a complete system** and also as **a total system** of base orders.

NOTE that, such an order is in general neither required to be complete nor
total. That is, the above order may in principle have more than one branch.
However, since the focus of this discussion is on pre-order traces, and since
there is already a complete path (from DTR to DPR), there is currently no need
to investigate if **a partial system** with more branches could exist and/or
could even be supported as a system of base orders.

Note that, in a complete partial system, each branch would have to end in the
trival order as its leaf order. That is, due to its empty set of edges, the
**trivial order** is related to other orders in a similar fashion as the empty
set is related to every other set. Because of that, and strictly speaking, the
above order can not have actual branches but "parallel/concurrent" paths, each
of which begins in DPR and ends in DTR. (recall - still a partial order).
