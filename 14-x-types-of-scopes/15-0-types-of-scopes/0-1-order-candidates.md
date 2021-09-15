
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (aka. **the processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
distinct implementations can be guaranteed to produce the exact same result.

* a tag soup is an encoding of the processing order

Recall that each scope is defined as an open interval (i.e. an induced suborder)
such that it begins with its defining node and includes every other node that
is subsequent to it. Even though a pre-order trace may still be used as the
base order of such intervals, the following will focus on finding restrictions
all base order candidates must satisfy.

* any base order is a (proper) suborder to the processing order

Since any scope over the doctree's pre-order trace will end in the document's
last node, any alternative base order is in general such that the scopes over
it will end before the document's last node.

* scopes are **intervals over a (proper) suborder to the pre-order trace**
* any super-order is order-preserving to its suborders
* any suborder is embedded into its super-order

Since the scope of a property follows the stream-based perspective (begins with
a defining node, ends with a last node, contains every other node in between),
each scope is a substring to the processing order.

* any scope is a **substring** to the pre-order trace
* any base order must be such that the scopes over it are substrings

Note that one should not assume that any substring can be supported. This rule
must therefore be understood as a mere restriction (i.e. **an upper boundary**)
of what can be supported. That is, further restrictions such as the following
may still apply.

<!-- ======================================================================= -->
## trivial base orders

Since a defining node may in general be the first and also the last node in
its scope, the trivial suborder (i.e. the document's set of nodes, but with
an empty set of edges) is a viable alternative as a base order.

* the **trivial suborder** of a pre-order trace is a viable base order
* aka. **the trivial base order**

Note that, due to having no edges at all, there is no node in a trivial order
that has another node subsequent to it. Any scope over a trivial suborder
therefore only consists of its defining node. Because of that, any scope over
the trivial base order is **a 1-element substring** to the processing order.

Note that any non-trivial processing order and its trivial suborder always
are two viable base orders. Because of that, any non-trivial processing order
allows to define **a set of base orders** such that any scope is in regards
to one of these base orders.

<!-- ======================================================================= -->
## distinct and unqiue scopes

Recall that any scope is defined as an open interval over a base order that
begins with its defining node (i.e. a single node that is intended to be the
scope's very first node - i.e. a root). Based on that, any scope can insofar
be described as unique since each scope then has a distinct starting point.

* the scopes over a base order must be **unique**

Note that a node can not become the root of a scope, if it were a node in a
cycle and as such subsequent to itself. Since there is no real starting point
to a cycle, and since any node can potentially be used as the defining node
of a scope, base orders must be required to be acyclic.

* a base order **must be acyclic**

Note that any suborder to a tree order is inherently acyclic. Because of that,
and due to the overall context (i.e. document trees), this requirement can be
understood to be auto-satisfied in the context of this discussion.

A set of base orders should in general be such that no scope over a base order
in it is equal to the scope of another base order.

* the scopes over distinct base orders should be distinct
* there should be no two base orders such that they have equal scopes

Note that the scope over the last node of a processing order is equal to the
scope of that node over the trivial base order. Because of that, the latter
can not be understood as an absolute requirement. Instead it must be understood
as **a guidance rule** intended to reduce the overall amount of exceptions.
