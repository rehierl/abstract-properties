
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (i.e. **the processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
implementations can be guaranteed to produce the exact same results.

* a tag soup encodes and visualizes a containment order
* a tag soup encodes and visualizes the processing order

Note that definitions in the context of a tag soup are in regards to the
processing order and the suborders it contains, not in regards to the
tag-based syntax itself (i.e. some specific representation).

<!-- ======================================================================= -->
## the processing order is a candidate

Recall that **scopes are defined as intervals over some base order** such
that each scope begins with its defining node and includes every other node
that is subsequent to it in that base order. Even though the processing
order may be used as a base order, the following discussion tries to focus
on the characteristics a base order must have - with the goal of trying to
find even more base order candidates.

* the processing order is a possible base order

<!-- ======================================================================= -->
## must appear as substrings

Since a scope must support **the stream-based perspective** (i.e. begins with
a defining node, ends with a last node, contains every other node in between),
each scope must be a substring to the processing order. Because of that, any
base order must be such that all of the scopes over it appear as substrings
to the processing order.

* each scope over a base order must be a **substring** to the processing order

Note that, even though each scope must appear as a substring to the processing
order, an arbitrary substring over the processing order does not necessarily
correspond with the scope over some base order. Because of that, the "each
scope must appear as a substring" description must be understood to describe
an upper boundary of the characteristics of a base order. Hence, further
restrictions have to be specified - i.e. a refinment process.

<!-- ======================================================================= -->
## the trivial base order is a candidate

Due to having no edges at all, no node in the **trivial suborder** has another
node subsequent to it in that suborder. Any scope over the trivial suborder
therefore only consists of its defining node. Because of that, any scope over
the trivial base order is **a 1-element substring** to the processing order.

* the trivial suborder is a possible base order

<!-- ======================================================================= -->
## must be a suborder

Since all the nodes in a scope must be subsequent to its defining node in the
processing order, a base order must be a suborder to the processing order. That
is, the processing order must be order-preserving in regards to a base order.
Otherwise, the defining node of a scope could not be guaranteed to appear first
in the processing order.

* any base order must be a suborder to the processing order

<!-- ======================================================================= -->
## must be downward-total

```
   |-> a -|       ||   ( r, a, c, b )
r -|      |-> c   ||       |--->|     s(a)
   |-> b -|       ||          |--->|  s(b)
```

If two nodes `a` and `b` were both next presequent to some node `c` in a base
order (i.e. more than one "parent"), then only one defining node of both scopes
(i.e. either `a` ex-or `b`) could be the first node in its scope. As a matter
of consequence, each base order must be downward-total, which is why any two
scopes over a base order must either be disjoint ex-or related (**DI-RE** -
i.e. scopes must not overlap).

* a base order must be a downward-total
* the scopes over a base order can not overlap

Recall that a tree order is downward-total. However, a tree order is also
restricted to one and only one root node. In contrary to that, a general
downward-total order may have any number of root nodes (i.e. a forest).

<!-- ======================================================================= -->
## must be acyclic

```
   |-> a -|       ||   ( r, a, b, c )
r -|      |-> c   ||       |------>|  s(a)
   |<- b -|       ||       |------>|  s(b)
```

Note that, from a strict point of view, node `a` has two source nodes - i.e.
node `r` and node `b`. Hence, that order is not downward-total. Apart from
that, and from a less strict point of view, not even node `c` can be understood
to have one dedicated next presequent node. After all, `a` is subsequent to
`b`, and `b` is subsequent to `a`.

If two nodes are nodes of some cycle, then both nodes have the same scope (i.e.
if seen as a set of nodes). Furthermore, only one of the nodes in such a cycle
can be such that its scope begins with its defining node in the processing
order. After all, each substring to that order has one and only one first node.
Because of that, a base order must be acyclic.

* a base order must be acyclic
* all the scopes over a base order must be distinct from one another

Note that **a suborder to a total order can not have any cycles** since that
would require the total order to be cyclic, which would be in conflict with
the order being total. After all, a total order is defined as a partial order,
which is defined to be anti-symmetric.

<!-- ======================================================================= -->
## unique scopes, equal scopes

Since a base order must be acyclic, and since scopes can not overlap each other,
the scopes over a base order must consequently be unique. After all, each node
then allows to define one and only one open interval which has that node as its
offset in the processing order.

* all the scopes over the same base order are **unique**

Note that the last node of a processing order is special insofar as all the
scopes of that node (i.e. its scopes over all the base orders) are equal (i.e.
1-element scopes). Because of that, one can not require that all the scopes
over all the base orders must be distinct.

* scopes can not be required to be globally unique

<!-- ======================================================================= -->
## must cover all of the nodes?

Thus far, a base order is **not required to cover all of the nodes** in the
processing order. That is, a base order may in principle be restricted to
a proper subset of nodes.

However, a base order will in general cover all of the nodes. After all, the
nodes not included would then remain without a scope over that base order.
(In the sense that the base order could then not provide such a definition,
which a design would then have to take into account).

<!-- ======================================================================= -->
## must be a tree order?

Recall that a base order is **not required to be a tree order**. After all,
the trivial suborder is undoubtedly a possible base order that has one root
per node. However, the question is if a base order (i.e. a forest) with edges
might be possible that still has more than one root.

Note that this question seems to be related to the "Must a base order cover
all of the nodes?" question. After all, if there must be in general one root
only, then all the other nodes would have to be subsequent to that root.

<!-- ======================================================================= -->
## base order candidates thus far

Recall that the trivial suborder, the unordered document tree, the ordered
document tree and the processing order all contain all of the nodes of the
document tree. Furthermore, these orders are suborders to the processing
order and each scope over these orders appears as a substring to that order.
Because of that, all of these orders are possible base orders.

* the trivial suborder (DTR) is a possible base order
* the unorderd document tree (DTU) is a possible base order
* the ordered document tree (DTO) is a possible base order
* the document tree's pre-order trace (DPR) is a possible base order
