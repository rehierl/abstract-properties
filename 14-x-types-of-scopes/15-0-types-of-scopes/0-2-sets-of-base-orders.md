
<!-- ======================================================================= -->
# sets of base orders

A processing order and its trivial suborder both represent viable base orders.
Because of that, any processing order allows to define **a set of base orders**
such that any scope in the context of that processing order is in regards to
one of the base orders it contains.

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
* may include the trival order
* may include the processing order
* may include other base orders

Note that a type system can be understood such that it effectively defines the
kinds of scopes that are allowed (i.e. can be supported) in a given context.

<!-- ======================================================================= -->
## an order of base orders

Recall that, in the context of this discussion, the doctree's pre-order trace
must be seen as the **processing order** and the doctree's tag soup as an
encoding of that order. Because of that, definitions in regards to a tag soup
are effectively definitions in regads to the processing order. Finally, and
since scopes are defined to be consistent with a stream-based point of view,
**any scope over a base order must be a substring** to the processing order.

```
TO --> UDT --> ODT --> PO
|< minimal     maximal >|
```

Recall also that the processing order (PO) is **a linear extension** to the
ordered doctree (OT), the unordered doctree (UT) and consequently also to the
trival sub-order (TO). And like any super-order, the processing order is order
preserving to each of its suborders, including the trivial suborder.

Note that a partial/linear extension is defined as the process of refining
the order of some source order. In contrary to that, the above use of "linear
extension" refers to the result of such a process. This usage must therefore
be understood to indirectly refer to the combination of extensions which allow
to transition from the source order to the resulting order. That is, a combined
process is, or can be expected to exist.

```
PO --> ODT --> UDT --> TO
|< maximal     minimal >|
```

Recall that the order relation of a processing order is total and therefore
transitive. With that in mind, an extension process can be understood such that
**a subset of edges** of the total order relation is added to a pre-existing
order relation. A transitive closure is then performed on the merger in order
to form the resulting order relation, which may possibly be an intermediate
order relation.

Due to the above, one can define an order `P(O,<)` over a set of node orders
`O` such that it is based on a containment order over the sets of edges `E()`
in each order relation.

* `P(V,<)` such that each `(v in V)` is a node order over `N`
* `(a < b) := (E(a) superset-of E(b))`

Since the focus of this discussion is on the processing order of a document
tree, order `P` has the processing order PO (i.e. the pre-order node order)
as its root node/order.

Note that the above order (PO to TO) is complete and total. That is, it
effectively descripes a step-wise extension from the trival order to the
prodessing order. Because of that, the corresponding system may be described
as **a complete system** and also as **a total system** of base orders.

NOTE that, such an order is in general neither required to be complete nor
total. That is, the above order may in principle have more than one branch.
However, since the focus of this discussion is on pre-order traces, and since
there is already a complete path (from the trivial order to the processing
order), there is at this point no need to investigate if **a partial system**
with multiple complete branches could exist and/or could even be supported
as a system of base orders.

Note that, in a partial system, each branch would have to end in the trival
order as its leaf. That is, due to its empty set of edges, the **trivial order**
is related to other orders in a similar fashion as the empty set is related
to every other set. Because of that, and strictly speaking, the above order
can not have actual branches but "parallel/concurrent" paths each of which
begins in PO and ends in TO. (Recall - still a partial order).
