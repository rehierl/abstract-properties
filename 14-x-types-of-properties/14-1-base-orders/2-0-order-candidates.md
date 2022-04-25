
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (i.e. **the processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
implementations can be guaranteed to produce the exact same results.

* a tag soup encodes and visualizes a containment order
* a tag soup encodes and visualizes the processing order

Note that definitions in the context of a tag soup are therefore in regards
to the processing order and the suborders it contains, not in regards to the
tag-based syntax itself (i.e. some specific representation).

<!-- ======================================================================= -->
## the processing order is a candidate

Recall that **scopes are defined as intervals over some base order** such that
each scope begins with its defining node and includes every other node that is
subsequent to it in that base order. Even though the processing order may be
used as a base order, the following tries to focus on the characteristics a
base order must have - with the goal trying to find even more order candidates.

* the processing order is a possible base order

<!-- ======================================================================= -->
## must appear as substrings

Since a scope must support **the stream-based perspective** (i.e. begins with
a defining node, ends with a last node, contains every other node in between),
each scope must be a substring to the processing order. Because of that, any
base order must be such that all the scopes over it appear as substrings to
the processing order.

* each scopes over a base order must be a **substring** to the processing order

Note that, even though each scope must appear as a substring to the processing
order, an arbitrary substring over the processing order does not necessarily
correspond with the scope over some base order. Because of that, the "each
scope must appear as a substring" description must be understood to describe
an upper boundary of the characteristics of a base order, which is why further
restrictions have to be specified (i.e. a refinment process).

<!-- ======================================================================= -->
## the trivial base order is a candidate

Due to having no edges at all, no node in the **trivial suborder** has another
node subsequent to it in that suborder. Any scope over the trivial suborder
therefore only consists of its defining node. Because of that, any scope over
the trivial base order is **a 1-element substring** to the processing order.

* the trivial suborder is a possible base order

<!-- ======================================================================= -->
## must be a suborder

Since all the nodes in a scope must be subsequent to its defining node in
the processing order, a base order must be a suborder to the processing order.
That is, the processing order must be order-preserving in regards to a base
order. Otherwise a scope's defining node can not be guaranteed to appear
first in the processing order.

* any base order must be a suborder to the processing order

<!-- ======================================================================= -->
## must be acyclic

If two nodes were nodes of the same cycle, then both nodes would have the exact
same scope (i.e. the same set of nodes). Furthermore, only one of the nodes in
such a cycle could be such that its scope would begin with its defining node in
the processing order. After all, each substring to that order has one and only
one first node. Because of that, a base order must be acyclic.

* a base order must be acyclic
* all the scopes over a base order must be distinct from one another

Note that **a suborder to a total order can not have cycles** since that would
require the total order to be cyclic, which would be in conflict with the order
being total. After all, a total order is defined as a partial order, which is
defined to be anti-symmetric.

<!-- ======================================================================= -->
## must be downward-total

If two nodes `a` and `b` were next presequent to some node `c` in a base order
(i.e. more than one "parent"), then only one defining node of the two scopes
(i.e. either `a` ex-or `b`) could be the first node to its scope in the
processing order. That is, the other scope could not be a substring to the
processing order since the other defining node would have to appear somewhere
in between its nodes. As a matter of, a base order must be downward-total,
which is why any two scopes over a base order must either be disjoint ex-or
related (i.e. **DI-RE** - i.e. scopes can not overlap).

* a base order must be a downward-total
* the scopes over a base order can not overlap

Recall that a tree order is downward-total. However, a tree order is restricted
to one and only one root node. In contrary to that, a general downward-total
order may have any number of root nodes (i.e. a forest).

<!-- ======================================================================= -->
## unique scopes, equal scopes

Since a base order must be acyclic, and since scopes can not overlap each other,
the scopes over the same base order are, as a matter of consequence, unique.
After all, each node allows to define one and only one open interval which has
that node as its offset.

* all the scopes over the same base order are **unique**

Note that, since the scope of the last node of a processing order is equal to
the scope over the trivial base order, one can not require that all the scopes
over all the base orders must be distinct.

* scopes can not be required to be globally unique

<!-- ======================================================================= -->
## must cover all of the nodes?

Thus far, base order is **not required to cover all of the nodes** in the
processing order. That is, a base order may in principle be restricted to a
proper subset of nodes. It should at this point be obvious that a base order
should cover all of the nodes. After all, the nodes not included would then
remain without a scope over such a base order.

<!-- ======================================================================= -->
## must be a tree order?

Recall that a base order is **not required to be a tree order**. After all,
the trivial suborder is undoubtedly a possible base order that has one root
per node. However, the question is if a base order with one or more edges
might be possible that still has more than one root.

Note that this question seems to be related to the "Must a base order cover
all of the nodes?" question. After all, if there must be one root only, then
all the other nodes must be subsequent to that root. Otherwise, there would
be a conflict since the base order would then have more than one root.

<!-- ======================================================================= -->
## base order candidates thus far

Recall that the trivial suborder, the unordered document tree, the ordered
document tree and the proessing order all contain all of the nodes of the
document tree. Furthermore, all of these orders are suborders to the
processing order and each scope over these orders appears as a substring
to the processing order. Because of that, all of these orders are possible
base orders.

* the trivial suborder (DTR) is a possible base order
* the unorderd document tree (DTU) is a possible base order
* the ordered document tree (DTO) is a possible base order
* the document tree's pre-order trace (DPR) is a possible base order
