
<!-- ======================================================================= -->
# sets of base orders

A processing order and its trivial suborder are both possible base orders.
With that in mind, any processing order can be understood to be associated
with **a set/system of base orders** such that any scope in that system is
based on one of the base orders it contains.

Depending on the requirements of a particular context, such a system may or
may not include the trivial base order. Likewise, it may or may not include
the processing order. And finally, it may or may not include even more base
orders in addition to the afore mentioned ones. Hence, even though a system
can be expected to contain at least one base order, a system can in general
not be required to include any base order in particular - it entirely depends
on the requirements of a given context.

A system of base orders ...

* can be expected to be non-empty
* may include the trival suborder
* may include the processing order
* may include further base orders

Note that the purpose a system of base orders is obviously to cover all of
the base orders over which scopes may be formed. As a matter of consequence
**a scope must be considered invalid**, if the system is not defined to
include the scope's base order as a base order.

* a scope over any order not included must be considered invalid

<!-- ======================================================================= -->
## the use of "linear extension"

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Recall that the processing order (DPR) is **a linear extension** to the
ordered doctree (DTO), the unordered doctree (DTU) and also to the trival
suborder (DTR). And like any super-order, the processing order is order
preserving to all of these suborders.

Recall that an order extension is defined as the refinement of some source
order by embedding a suborder into it. In contrary to that, the above use of
"linear extension" refers to the result of such a process. This usage must
therefore be understood to implicitly refer to the combination of one or more
extensions, which allow to transition from the source order to the resulting
order. That is, a chain of extensions can be expected to exist.

Note that the order relation of the processing order is total and transitive.
With that in mind, an extension can be understood such that a subset of edges
of the total order relation is embedded into a pre-existing order relation.
A transitive closure is then performed on the result in order to form the
resulting order relation, which may be an intermediate order relation - i.e.
not necessarily the processing order.

Note that, similar to entropy in physics, the trivial suborder can be
understood to have **minimal order** (or max disorder). In contrary to that,
the document tree's pre-order trace can be understood to have **maximal order**
(or min disorder). Put differently, the order of the document tree's pre-order
trace can not be extended any further without introducing a conflict (i.e.
symmetric edges). After all, the underlying order relation already has an edge
in between any two nodes.

<!-- ======================================================================= -->
## an order of base orders

Based on the above, one can define an order `P(V,<)` over a set of base orders
`V` such that it is a containment order over the sets of edges `E()` in each
order relation.

* `P(V,<)` such that each `(v in V)` is a base order
* `(a < b) := (E(a) superset-of E(b))`

With the processing order of a document tree in mind, the resulting order would
have the document tree's pre-order node order DPR as its root, and the trivial
suborder as its only leaf.

Note that the orientation of the edges in this order relation is reversed
to the above pictogram. That is because, since an empty set is a subset to
every other set, one would otherwise end up with a non-linear order. For a
proper definition, one would have to use an order-operator that is based on
the existence of "an order embedding does exist from A to B". As a matter of
simplification, it is assumed that the overall point of this simplification
is be clear - i.e. an order relation can be defined.

<!-- ======================================================================= -->
## TODO - remarks - extended systems?

Note that the order visualized above (i.e. "DPR to DTR") is complete and total.
That is, it effectively descripes a step-wise extension from the trival suborder
DTR to the prodessing order DPR. Such a system may in general be described as
**a complete system of base orders**.

Note that such an order is in general not required to be linear. That is,
such an order may in principle have more than one branch. However, since the
focus of this discussion is on the pre-order trace of a document tree, and
since there is already a complete path (from DTR to DPR), there is at this
point no need to determine if **a partial system** with more branches would
exist and/or if such a system of base orders would even be possible.
