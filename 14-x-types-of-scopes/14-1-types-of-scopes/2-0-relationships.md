
<!-- ======================================================================= -->
# relationships between base orders

Note that, in regards to the following, one needs to keep in mind that each
scope first and foremost defines a set of nodes. That one can used these sets
of nodes to form induced subgraphs is secondary to the following discussion.

<!-- ======================================================================= -->
## scopes and nodes

Depending on a given context (i.e. a particular set of base orders), any node
can in general be understood to be associated with several distinct non-empty
scopes. Conversely, any node can be understood to be located within more than
one scope.

* there is (in general) a **n:m relationship** between scopes and nodes

One might therefore suspect that a system of base orders allows to form
hierarchies of scopes based on the nodes the scopes have in common.

<!-- ======================================================================= -->
## scopes of the same base order

The relationships between the scopes over the same base order have been
discussed already. After all, one can state that each node tree corresponds
with a hierarchy of scopes, which is why each scope is either disjoint exor
related (i.e. DI-RE) to every other scope over the same base order.

* DTU/DTO - a partial hierarchy of scopes
* DPR - a total hierarchy of scopes

<!-- ======================================================================= -->
## ( DTU vs. DTO )

Each scope over DTU is disjoint exor related (i.e. **DI-RE**) to every other
scope over DTO.

TODO - In addition to that one can clarify that no scope over DTU is a proper
superset to any scope over DTO.

* for some `u := [u,*]` over DTU, and some `o := [o,*]` over DTO
* `(u disjoint-to o) exor (u related-to o)` is always true
* `(u superset-of o)` is never true for `(u != o)`

From the perspective of a scope over DTO one can state the same. That is, each
scope over DTO is disjoint exor related to each scope over DTU. However, one
can clarify that no scope over DTO is a proper subset to any scope over DTU.

* `(u disjoint-to o) exor (u subset-of o)` is always true

Note that, since no scope over DTU can be a proper superset to a scope over
DTO, each such scope can be described as a **building block** over DTO. That
is, any scope over DTO can be described to consist of **generic units** over
DTU. Based on that, the base order DTO can be described to have a certain
**level of granularity**.

* any scope over DTO is **a non-empty sequence of scopes over DTU**

Note that the union of all scopes over DTU and DTO form a hierarchy of scopes.
That is, such a union has **no overlapping scopes**.

<!-- ======================================================================= -->
## ( DTU vs. DPR )

Recall that each scope over a processing order will by default end in a leaf.

```
          |- [n,*] -------------->|
.. <p> .. <n> fc .. x .. lc .. </n> ns .. </p> .. </r>
   |- [p,*] ---------------------------------------->| - superset
                    |- [x,*] ----------------------->| - overlaps (!)
                                    |- [ns,*] ------>| - disjoint
```

Each scope `s(n)` over DTU is either disjoint-to, a subset-of, or overlaps a
scope `s(a)` over DTO (i.e. **DI-RE-OV**).

```
.. <p> .. <n> fc .. x .. lc .. </n> ns .. </p> .. </r>
          |- [n,*] -------------->|
                    |- [x,*] ----------------------->| - overlaps (!)
```

As visualized above, a scope over DTU will overlap a scope over DPR, if the
latter reaches out of the former.

Note that the smallest units in the intersection between a scope over DTU
with a scope over DTO are the nodes of the document tree. Because of that,
such an intersection has **no inner structure** (i.e. **no granularity**).

Note that the possibility of overlapping scopes **prevents any grouping**.
One can therefore in general not use a pair of tags to group the contents
of a scope over DTU that is marked using a scope over DPR.

<!-- ======================================================================= -->
## ( DTO vs. DPR )

Note that the same observations can be made in regards to the relationship
between a scope over DTO and a scope over DPR. That is, such as scope is
either disjoint-to, a subset-of, or overlaps the other scope (DI-RE-OV).

<!-- ======================================================================= -->
## remarks

Note that, since the intersection between a scope over DTU and a scope over
DPR can in general not be grouped using a pair of tags, it is **ill advised**
to allow the use of DPR scopes **for content-related properties**. That is,
scopes over DPR can and should only be allowed for properties such as global
variables and disallowed for anything else.

Note that the above is obviously in regards to complete default scopes. Despite
that, one must keep in mind that allowing content-related scopes over DPR will
make it in general **impossible to reliably group content**.

Note that, provided that scopes over DPR are disallowed for content-related
properties, one can state that a scope over DTO either contains a node and all
its descendants in DTU **exor none at all**.
