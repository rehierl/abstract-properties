
<!-- ======================================================================= -->
# relationships between base orders

Depending on a given context (i.e. a particular set of base orders), any node
can in general be understood to be the defining node of several scopes. Also,
any node can be understood to be a content node in more than one scope. Because
of that, there is a **n:m relationship** between scopes and nodes.

Furthermore, since nodes are shared across multiple scopes, **hierarchies**
of scopes can be formed over the scopes of the same base order. That is, one
can state that each node tree corresponds with a hierarchy of scopes, which
is why each scope is either disjoint exor related (i.e. **DI-RE**) to every
other scope over the same base order.

* DTU/DTO - a partial hierarchy of scopes
* DPR - a total hierarchy of scopes

Since the nodes of a document may be **shared across multiple base orders**,
one might suspect that hierarchies over multiple base orders can be formed.

Recall that each scope first and foremost defines a simple set of nodes. It
is secondary to the following discussion that these sets can be used to form
induced subgraphs.

<!-- ======================================================================= -->
## ( DTU/DTO vs. DPR )

```
          |-DTU[n]---------->|
.. <p> .. <n> fc .. lc .. </n> ns .. </p> .. </r>
   |-DPR[x]------------------------------------>| - superset
                    |-DPR[x]------------------->| - overlaps (!)
                               |-DPR[x]-------->| - disjoint
```

Each scope over DPR (i.e. `DPR[x]`) is either disjoint-to, related-to,
or overlaps a scope `DTU[n]` (i.e. **DI-RE-OV**).

In addition to that, the smallest units in the intersection between a scope
over DTU with a scope over DPR are the nodes of a doucment (i.e. 1-element
groups of nodes). The intersection between such scopes therefore has in
general **no inner structure** (i.e. **no granularity**) that can be relied
upon.

Because of that, one can in general not use pairs of tags (i.e. scopes over
DTU) to **enclose the intersection** between scopes. One can therefore state
that having **overlapping scopes prevents grouping by tags**.

Note that it is at this point non-relevant that DPR scopes by default always
end with a document's last node. What counts is that a DPR scope may begin
inside of a DTU scope and may end with a node in the outside, subseqeuent
to the DTU's last node.

Note that the same observations can be made in regards to the relationship
between a scope `DTO[n]` and a scope `DPR[x]`. That is, a DPR scope is either
disjoint-to, related-to, or overlaps a DTO scope.

Since **the intersections between DTU scopes and DPR scopes** can in general
not be grouped using pairs of tags, it is **ill advised** to allow the use of
**DPR scopes for content-related properties**. That is, scopes over DPR should
only be allowed for properties such as (e.g.) **global variables** and
disallowed for anything else.

<!-- ======================================================================= -->
## ( DTO => DTU )

Note that the following resembles a sampling process of scopes over DTO in
regards to some scope `DTU[n]`. That is, in regards to a "stationary" DTU
scope, certain DTO scopes are examined in regards to their relationship with
that DTU scope.

```
               p
               |
 ----------------------------
 | .. |        |       | .. |
 |    | |-DTO--|-------|----|-|
 fs  ps ||-DTU-|-----| |    | |
        ||     n     | ns  ls |
        ||     |     |        |
        ||  -------  |        |
        ||  | ... |  |        |
        ||  fc   lc  |        |
        ||-----------|        |
        |---------------------|
```

A scope over DTO that has a descendant of node `n` as its root,
is a **subset** to `DTU[n]`.

* `(DTO[x] subset-of DTU[n])` for `(x in D(n))`

A scope over DTO that has a subsequent sibling of `n` as its root,
is **disjoint** to `DTU[n]`.

* `(DTO[x] disjoint-to DTU[n]` for `(x in [ns,*] over co(p))`

A scope over DTO that has node `n` or one of its presequent siblings
as its root (e.g. a heading), is a **superset** to `DTU[n]`.

* `(DTO[x] superset-of DTU[n])` for `(x in [fs,n] over co(p))`

A scope over DTO that has an ancestor of `n`, or one of their presequent
siblings as its root, is a **superset** to `DTU[n]`.

Note that the latter nodes are all nodes in the rooted path `rp(n)` over
DTO. That is, `DTO[x]` is a superset to `DTU[n]`, if `x` is equal to `n`
or an ancestor of `n` over DTO.

Every other scope `DTO[x]` is **disjoint** to `DTU[n]`. That is because
`x` then has no descendant in DTO which is also a node in `DTU[n]`.

Since no scope over DTO overlaps any scope over DTU, each scope over DTO
is disjoint exor related (i.e. **DI-RE**) to every scope over DTU.

<!-- ======================================================================= -->
## ( DTU => DTO )

Note that the following will continue the afore mentioned sampling process.
This time however with a DTO scope as the "stationary" scope.

```
|-DTU[p]-----------------------------------|
|                  |-DTO[n]--------------| |
| p -> (fs .. ps) -|-> n -|-> (ns .. ls) | |
|                  |      |-> (fc .. lc) | |
|                  |---------------------| |
|------------------------------------------|
```

A scope over DTU that has any node in `DTO[n]` as its root,
is a **subset** to `DTO[n]`.

* `(DTU[x] subset-of DTO[n])` for `(x in DTO[n])`

A scope over DTU that has any node in `DTO[fs,n)` as its root,
is **disjoint** to `DTO[n]`.

* `(DTU[x] disjoint-to DTO[n])` for `(x in DTO[fs,n))`

A scope over DTU that has an ancestor `a` of `n` in DTU as its root,
is a **superset** to `DTO[n]`.

* `(DTU[x] superset-of DTO[n])` for `(x in A(n))`

Note that a scope over DTU, that has any node in `rp(p)` over DTU as its
root is a superset to DTO, if `p` is the parent of `n` over DTU.

Every other scope `DTU[x]` is **disjoint** to `DTO[n]`. That is because
there is no descendant of `x` in DTU, which is also a node in `DTO[n]`.

Since no scope over DTU overlaps any scope over DTO, each scope over DTU
is disjoint exor related (i.e. **DI-RE**) to every scope over DTO.

<!-- ======================================================================= -->
## remarks

Recall that the use of **DPR scopes** (everything until the very end) is ill
adviced in regards to grouping content. That is because it is in general not
possible to group that content using the tag-based syntax. DPR scopes are
therefore only useful for properties such as (e.g.) **global variables**.

Likewise, **DTR scopes** (single nodes only) are similar to DPR scopes since
they do not provide any notable structure. Put differently, DTR scopes can not
be used for content-related properties since content consists of more than one
node. Scopes over DTR can therefore only be used for properties such as (e.g.)
node **identifiers**, not for anything else.

Consequently, the only types of scopes that can be used to **group content**
by default are **DTU and DTO scopes**. That is, only two types of scopes are
available to define how content can be grouped.

```
DTO[x] -to- DTU[n]
=======================================================
r -> .. -> p -> fs -> .. -> ps -> n -|-> ns -> .. -> ls
                                     |-> fc -> .. -> lc
|---------------------------------|      |------------|
 superset-of                         subset-of / disjoint-to
```

```
DTU[x] -to- DTO[n]
=======================================================
r -> .. -> p -> fs -> .. -> ps -> n -|-> ns -> .. -> ls
                                     |-> fc -> .. -> lc
|----------------------------|    |-------------------|
 superset-of / disjoint-to         subset-of
```

Since **no DTU scope overlaps a DTO scope** and vice versa, any DTO scope can
by default be said to either contain a node and all of its dedscendants over
DTU **exor none at all**.

Because of that, **one can describe a DTO scope as a sequence of DTU scopes**.
That is, a DTO scope can be described as a sequence of **building blocks**
and therefore to have **a certain level of granularity**.

Note that one can not describe a DTU scope in regards to the **DTO scopes**
it contains. That is because the DTO scope of a subsequent child is a
suffix to the DTO scope of a presequent sibling. That is, these DTO scopes
**can not be guaranteed to be disjoint**, which is essential to being able
to describe a thing as a group of distinct things.
