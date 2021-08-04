
<!-- ======================================================================= -->
# pre-order

An ordered set `P := (V,R)` that has an order relation which is
**reflexive and transitive** can be described as an ordered set that
is associated with a **(simple) preorder** order relation. Based on
that, the ordered set itself can be described as a (simple) preorder.

* any (simple) preorder is reflexive and transitive

Note that a preorder can be understood as an ordered set that is missing one
or more additional characteristics which would turn it into an actual order.
Put differently, a preorder is an ordered set that isn't seen as an order that
could be considered "complete". That is, one can read "pre-" as referring to
"not quite complete".

An ordered set `Q := (V,R)` that has an order relation which is
**irreflexive and transitive** can be described as an ordered set that
is associated with a **strict preorder** order relation. Based on that,
the ordered set itself can be described as a strict preorder.

* any strict preorder is irreflexive and transitive

Note that, depending on a given context, the description as "preorder" may
refer to a preorder that could be "simple" or "strict". Put differently,
one can not always assume "simple preorder" if a description is reduced to
"preorder", since it does tend to get tedious in a given context to refer
to each and every preorder as being "strict", especially if the focus of
a discussion is almost exclusively on strict preorders. When in doubt, a
preorder should however be clarified as "simple" or "strict". In that
regards, one should also take the semantical expression into account that
is associated with a given preorder.

Note that any order, simple or strict, is considered a preorder. Because of
that, the description as "preorder" is in general ignored. The definition of
"preorder" must therefore be understood to define the minimum requirements an
order relation must satisfy (i.e. "reflexive/irreflexive" and "transitive")
in order for it to be an actual order relation.

**Note that any order relation is required to be transitive**. In combination
with the default sequence-based semantics, any transitive closure of a relation
can be described as the order relation of some ordered set.

Note that an order relation that has an empty set of edges (i.e. `P := (V,{})`)
will be describes as **a degenerated order relation**. (In that regards, an
empty set of edges is considered to be transitive).

<!-- ======================================================================= -->
## reflexive, irreflexive, strict

Recall that a **reflexive** relation has a **loop** for each of its vertices.
In contrary to that, a relation that is **irreflexive** (aka. **strict**) has
no such loop at all.

* reflexive := `aRa` is true for any `(a in V)`
* irreflexive := `aRa` if false for any `(a in V)`

Note that the lower-than order `P := (N,<)` over the set of natural numbers is
irreflexive. After all, `(a < a)` (or `aRa`) is not true for any `(a in N)`.
In contrary to that, the lower-than-or-equal order `Q := (N,<=)` is reflexive.

Note that there are order relations that can be considered to be in between
"reflexive" and "irreflexive". However, such orders are non-relevant to the
overall context of this discussion. That is, in the context of this discussion,
an order relation is either reflexive, ex-or irreflexive - i.e. either all
vertices have loops, ex-or none at all.

<!-- ======================================================================= -->
## transitive relations

A relation `R := (V,G)` that is **transitive** has an edge `aRc` for each pair
of edges `aRb` and `bRc`.

* transitive := if `aRb` and `bRc` are both true, then `aRc` must also be true

Note that `aRc` can be understood as an edge that represents a path over the
edges `aRb` and `bRc`. As such, `aRc` connects the endpoints of that path.
Based on that, a transitive relation can be described as a relation that has
an edge for each and every path that can be formed over its edges. In that
regards, a transitive relation can be described as being **complete** since
no transitive edge can be derived from existing ones that is still missing.

Note that the lower-than order `P := (N,<)` over the set of natural numers is
transitive. After all, a number `a` that is lower-than another number `b` is
also lower-than any number to which `b` is a lower number.

Note that any edge that will be removed by the transitive reduction of a
transitive relation, will be referred to as **a transitive edge**. As such,
the term can be understood to refer to those edges that can be derived based
upon the construction of a path over the edges that remain in the transitive
reduction.
