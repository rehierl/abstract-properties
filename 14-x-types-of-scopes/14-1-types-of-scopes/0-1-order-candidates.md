
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (aka. **the processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
distinct implementations can be guaranteed to produce the exact same result.

* a tag soup encodes and visualizes a processing order

Note that definitions in the context of a tag soup are therefore in regards
to the processing order and the suborders it contains, not in regards to the
tag-based syntax (i.e. some specific syntax) itself.

Recall that **scopes are defined as intervals over a base order** such that
each scope begins with its defining node and includes every other node that
is subsequent to it in that base order. Even though the processing order may
be used as a base order, the following tries to focus on those characteristics
a base order must have - with the goal of allowing to find more base orders.

* the processing order is a viable base order

Since a scope **follows the stream-based perspective** (begins with a defining
node, ends with a last node, contains every other node in between), each scope
is a substring to the processing order. Because of that, any base order must
be such that all scopes over it appear as substrings to the processing order.

* the scopes over a base order must be **substrings** to the processing order
* each substring must begin with the scope's defining node

Note that, even though each scope must correspond with a substring over the
processing order, an arbitrary substring over the processing order does not
necessarily correspond with the scope over some base order. Because of that,
the "any scope must appear as a substring" must be understood to describe
**an upper boundary** of the characteristics of a base order. In addition
to that, further restrictions may still follow (i.e. a refinment process).

<!-- ======================================================================= -->
## the trivial base order

Due to having no edges at all, no node in the **trivial suborder** of a doctree
has another node subsequent to it. Any scope over the trivial suborder therefore
only consists of its defining node. Because of that, any scope over the trivial
base order is **a 1-element substring** to the processing order.

* the trivial suborder of the doctree is a viable base order

<!-- ======================================================================= -->
## remarks

Since all the nodes in a scope must be subsequent to its defining node in the
processing order, a base order must be a **suborder** to the processing order.
Otherwise a scope's defining node can not be guaranteed to appear first in the
processing order.

* any base order must be a suborder to the processing order
* any super-order is order-preserving to all of its suborders
* any suborder is embedded into its super-order

If two nodes were nodes of the same cycle, then both nodes would have the same
scope (i.e. the same set of nodes). Furthermore, only one of the nodes in such
a cycle could be such that its scope would begin with its defining node in the
processing order. Because of that, base orders must be **acyclic**.

* a base order must be acyclic
* all scopes over the same base order must be unique

Note that no suborder to a total order can be cyclic since that would require
the order to be cyclic. That however would be in conflict with the order being
total (i.e. a total order is acyclic).

<!-- ======================================================================= -->
## remarks

If two nodes `a` and `b` were next presequent to node `c` in a base order (i.e.
more than one "parent"), then either `a` would appear in between `b` and `c`
in the processing order, or `b` would appear in between `a` and `c`. Because
of that, one of the scopes could not be a substring to the processing order.
As a matter of consequence, a base order must be downward-total. That is, any
two scopes over a base order must be such that they are either disjoint exor
related (i.e. **DI-RE**). Since a base order must be a tree order, all the
scopes over the same base order are distinct.

* a base order must be a **tree order**
* all scopes over the same base order must be **unique**

Since the scope of the last node of a processing order is equal to the scope
of that node over the trivial base order, scopes can not be required to be
"globally unique". That is, one can not require that all the scopes over all
the base orders must be distinct.

* scopes over distinct base orders may be equal

<!-- ======================================================================= -->
## remarks

Note that the trivial suborder DTR, the unordered doctree DTU and the ordered
doctree DTO all contain all the nodes of the doctree. As such, these suborders
appear as substrings to the processing order.

Note that a base order is in general not required to contain all the nodes of
a doctree. That is, a base order may in principle be restricted to a subset of
nodes. It is however unclear at this point, if all the nodes of a base order
must form a substring to the processing order, or if that aspect is a mere
matter of consequence.
