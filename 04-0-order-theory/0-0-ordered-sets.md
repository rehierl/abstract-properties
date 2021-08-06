
<!-- ======================================================================= -->
# ordered sets

An ordered set (of elements) `P := (V,×)` is **a set of vertices** `V` that is
paired with **an order operator** `×`. As such, an ordered set is no simple
set, but a complex value/type.

The order operator `×`, with which an ordered set is associated, can be
described as a binary predicate that is defined to return true for a given
pair of vertices, iff the vertices can be described as being "in order". In
combination with an expression that defines the semantics of such an operator,
the order operator can be understood to define all of the relationships
between the vertices in an ordered set (i.e. the actual order).

* `(a × b) := (true|false)` for `(a,b in V)`

Some examples of order operators are:

* `(a < b) := ('a' is lower than 'b')`
* `(a < b) := (a presequent-to b)`
* `(a <= b) := ('a' is lower than or equal to 'b')`
* `(a <= b) := (a superset-of b)`

Note that the symbol of an order operator itself does not define the order.
Instead, one must see these symbols as representing the semantical expression
by which they are defined.

* `(a < b) := ('a' greater than or equal to 'b')`
* although possible, certainly not the best choice (!)

Since there is in general a limited set of symbols available, one must always
be aware of the "default" semantics that are in general associated with a given
symbol. In order to avoid unnecessary confusion, one should therefore choose
a symbol only if its default semantics "matches" the semantics of a particular
ordered set.

<!-- ======================================================================= -->
## order relation

Since the vertices of an ordered set can in principle be of any kind (e.g.
objects, colors, etc.) an ordered set is not required to represent any kind
of default/natural order. Because of that, it is not always be possible to
define an order operator based on a simple semantical expression. In such a
case one can still define an order operator based on a known order relation.

Since the order operator `×` of an ordered set `P := (V,×)` is defined as a
binary predicate, one can use the order operator to define an endo-relation
`R := (V, G)` such that the relation has an edge for each pair of vertices
that are considered to be "in order". Based on that, an order operator can
in general be used to define an order relation.

* `G := { (a,b) | (a × b) is true }`
* alternatively `aRb := (a × b)`

Conversely, one can use an endo-relation `S := (V,G)` to define the operator
of an ordered set. That is, the operator is understood to return true, iff `S`
has an edge for a specific pair of vertices. The relation used to define an
order operator can therefore be described as an order relation.

* `(a × b) := aSb`

One can therefore also describe and ordered set as a set of vertices `V` that
is paired with an order relation `S`. Since the set of vertices of an ordered
set can be understood to be equal to the set of vertices of the order relation,
each ordered set can itself be said to correspond with an order relation.

* `P := (V,×)` <=> `P := (V,G)`

Note that an endo-relation may be described as **an order relation**, if it
is either used to describe an existing order operator, or if it used to define
such an order operator. Put differently, an order relation is an endo-relation
that is used to describe or define the relationships within an ordered set.

Note that, due to the above, the operator-based definition can be understood
to provide a definition that can be considered "more intuitive". However,
since the operator symbols that are available are in general associated with
a default/natural order in regards to a particular set of elements, the
relation-based definition seems "more generic" and as such "less misleading".

<!-- ======================================================================= -->
## cover relation, hasse diagrams

Note that the reflexive transitive reduction of an order relation can be
described as **the cover relation** of an order relation.

Note that **a hasse diagram** is the drawing of an order's (reflexive) transitive
reduction. Hence, a hasse diagram can be said to visualize the cover relation
of an order and as such to "cover" an order relation.

<!-- ======================================================================= -->
## read "as is"

Note that the intention of this section is to point out that one needs to
**focus on those features that are defined, not on what isn't defined**.

In particular, two vertices that are incomparable are most distracting at first
since that aspect is non-existent in total orders, such as the default natural
order over the set of natural numbers, and because of that counter intuitive.
Once one manges to generalize one's own perception of "order", the existence of
incomparable vertices turns out to be almost secondary.

In addition to that, one should also try to "not invent features" an order
relation does not support. As an example, if `(a < b)` and `(b < a)` are both
true over a given order relation, then both endpoints can not be automatically
considered equal. That is because the order operator `<` does not include a
notion of equality.

However, one can still choose to derive a new order that does include a sense
of equality, based upon an order that does not. If such an option is chosen,
then one must keep in mind that both orders are not equal. That is, both orders
describe different "things".

<!-- ======================================================================= -->
## default sequence-based semantics

Since each ordered set can be understood to be associated with an order relation,
and since such an order relation consists of edges over vertices, one should by
default read each edge as a 2-element sequence of vertices. One can therefore
initially assume sequence-based semantics that are independent of the actual
elements within an ordered set. Based on that, one is more likely to read an
order relation "as is", since the sequence-based semantics are in general not
associated with any particular type of element.

* `(a < b) := (a presequent-to b)`
* `(a <= b) := (a presequent-to b) or (a equal-to b)`

Despite that, and in regards to the properties of a particular order relation,
one can still focus on semantics that are more specific. That is, in the
context of a particular order one can assume a mapping between the default
sequence-based semantics and the specific semantics of that order.

* `(a presequent-to b) <-> (a strict-superset-of b)`
