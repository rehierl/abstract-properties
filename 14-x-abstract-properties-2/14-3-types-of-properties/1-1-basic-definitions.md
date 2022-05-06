
<!-- ======================================================================= -->
## nodes - properties, keys, values

Every node `(n in N)` in a tree `T(N,E)` can be understood to have a set of
properties `P(n)` associated with it, and each property `(p in P(n))` can be
understood to describe some unique characteristic (e.g. id, color). Because
of that, a property can be understood to correspond with a pair of values,
each of which consists the unique key of a property (e.g. "id") and a value
(e.g. "id-1").

* `p := (k,v)` for `(p in P(n))`
* `p.k, p.key := k` and `p.v, p.value := v`

Since each node has a set of properties `P(n)` associated with it, a node can
be said to be marked or tagged with each property in its set of properties.
Furthermore, property `p` can be said to have value `v` in the context of `n`.

Note that the value of a property is expected to be concrete, which is why the
value of a property can not be undefined. Apart from that, the actual value of
a property is secondary to the following discussion since the focus will be on
whether a node has a given property set or not.

Based on the above, each node can be said to be associated with a set of keys
`K(n)` and a set of values `V(n)`.

* `K(n) := { p.k | (p in P(n)) }`
* `V(n) := { p.v | (p in P(n)) }`

Note that a property may in principle be associated with different values in
distinct nodes. Furthermore, each node may have one or more properties that
are associated with the same value.

* `(#K(n) == #P(n))` must be true
* `(#V(n) < #P(n))` may be true

Note that, even though it is not overly accurate, this discussion will treat
the term "property" as being synonymous to the key of a property. That is, a
property will be treated as two separate values (i.e. not as a combined unit):
a key (i.e. the property) and the value that is associated with it the context
of a given node.

* `n.p := v` if `((p,v) in P(n))`

<!-- ======================================================================= -->
## defined, exists, undefined

If node `n` is associated with property `p`, then the property's value can
be determined. Because of that, `p` can be understood to be `defined` in the
context of node `n` and can thus be said to exist in the corresponding tree.

* `is-defined(p,n) := (p in K(n))`

If `(p in P(n))` is true, then the following can be said:

* `p` is associated with `n`
* `p` is known to `n`
* `p` is set in regards to `n`
* `n` has `p` as a property
* `n` is marked/tagged with `p`

<!-- ======================================================================= -->
## properties - nodes, values

A property `p` can be understood to define a subset of nodes `N(p)` over the
set of nodes `N`. This set contains all the nodes to which `p` is known. Also,
`p` can be said to define a set of values `V(p)` that contains all the values
the property is associated with in these nodes.

* `N(p) := { n | (p in K(n)) for (n in N) }`
* `V(p) := { n.p | (n in N(p)) }`
* `(#N(p) >= 1)` and `(#V(p) >= 1)` are both true
* `(#V(p) <= #N(p) <= #N)` is true

<!-- ======================================================================= -->
## trees - keys, values

Similar to a node, a tree `T(N,E)` can be understood to be associated with a
set of keys `K(T)` and a set of values `V(T)`. In regards to a tree, the set
of keys is more relevant since it contains the keys of all the properties
that are known to one or more nodes.

* `K(T) := { k | (k in K(n)) for (n in N) }`
* `V(T) := { v | (v in V(n)) for (n in N) }`

If property `p` is known to nodes `a` and `b`, then the value it has in both
nodes can be compared. However, the result of such a comparison can not be
determined, if the property is unknown to one or both nodes. If that is the
case, then the result of such a comparison counts as being `undefined`.

* `(a.p == b.p)` is undefined, if `(p not-in K(a))` and/or `(p not-in K(b))`
* `(a.p == b.p)` is true, false or undefined

Two nodes are said to share a property, or to **have a property in common**,
if the property is known to both nodes, regardless of the values the property
has in both nodes. Because of that, a comparison of the values of a property
for equality in regards to two nodes is defined (i.e. true or false), if and
only if the property is known to both nodes.

* `is-shared(p,a,b) := (p in K(a)) and (p in K(b))`

This definition can be thought of as being extended such that it also applies
to a set of nodes `S`. That is, a property can be said to be shared in regards
to a group of nodes, if the property is known to all the nodes in that group.
Based on that, groups of nodes can be defined in terms of shared properties.

* `is-shared(p,S)` is true, if `is-shared(p,a,b)` is true for all `(a,b in S)`
