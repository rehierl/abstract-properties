
# mathematics / order theory (OT)

This chapter introduces ordered sets of elements, which are in general defined
similar to endo-relations as two-element tuples `O(V,×)` that consist of a set
of vertices `V` and a binary **order operator** `×`. This operator is defined
to return `true`, if the input vertices are understood to be in order.

* `(a × b) := true`, if `a` and `b` are in order.

<!-- ======================================================================= -->
## order relations

Since the focus of this discussion is on solely on finite sets of elements,
one can think of an ordered set to be defined based on an **order relation**
`P(V,E)` such that the set of edges `E` a directed edge for each pair of
vertices for which the order operator is understood to be true. Hence, the
edges in an ordered set need to be understood as a consequence of the order
operator, which describes a certain pre-defined type of relationship. Other
than that, there is no degree of freedom in regards to which connections do
exist and which ones don't.

* `E := { (a,b) | (a × b) }`

Note that, since an order relation may in general contain any number of
connections, visual representations tend to become excessive. Because of
that, only the **cover relation** will usually be visualized, since this
relation is defined as the reflexive transitive reduction of the underlying
relation.

<!-- ======================================================================= -->
## order types

The most basic aspect of an order relation is that it must be **transitive**.
That is, an Edge `aEb` must exist for any path `aPb` that can be formed.
Based on that, a transitive order relation can be understood to represent
a **preorder**.

Note that an order operator can be defined based on any endo-relation `G(V,E)`,
if it is defined based on the paths that can be formed over the edges in it.

* `(a < b) := aPb is true over G`
* `(a < b) := (a presequent-to b) over G`

Note that the focus of this discussion is solely on irreflexive (i.e. no
loops) preorder order relations, aka. **strict preorder**. As a matter of
consequence, any such order relation must be **acyclic**. That is because
transitivity would otherwise force the existence of symmetric edges and
even loops.

* preorder - a transitive endo-relation
* partial order (poset) - an a-symmetric preorder
* total/linear order (toset) - a trichotomous partial order

Note that, in the context of this discussion, further relevant definitions
are: induced suborder, order-preserving, order-embedding, downward-total,
partial/linear extension.

<!-- ======================================================================= -->
## general remarks

Note that in Graph Theory (GT), the set of Edges `E` of a graph does in general
not have such a strict definition. However, certain types of graphs may or may
not introduce requirements a set of Edges `E` is expected to satisfy. This core
difference suggests that **the focus of OT is on the set of vertices**, whereas
GT seems to focus more on "syntactic" characteristics.

Note that the cover relation of a poset may have vertices with
**more than one parent** (i.e. more than one incoming edge). Hence, the class
of all **tree orders** can be described as a sub-class of specialized posets.

Note that **intervals** can be defined over partial orders. As a matter
of consequence, the generalized definitions of **prefix**, **infix**
and **suffix** can be understood to still apply to non-linear orders.
