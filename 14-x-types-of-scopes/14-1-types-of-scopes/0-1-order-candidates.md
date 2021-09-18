
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (aka. **its processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
distinct implementations can be guaranteed to produce the exact same result.

* a tag soup encodes the processing order
* a tag soup can be used to visualize the processing order

Note that definitions in regards to a tag soup are therefore not in regards
to the tag-based syntax (i.e. some specific syntax), but in regards to the
processing order and the suborders it contains.

Recall that each scope is defined as an open interval such that it begins with
its defining node and includes every other node that is subsequent to it. Even
though the processing order may be used as a base order, the following tries
to focus on finding restrictions each such base order candidate must satisfy.

* the processing order is a base order candidate
* any base order is a (proper) suborder to the processing order

Since any scope over the processing order will end in the document's last node,
any alternative base order is in general such that the scopes over it will end
before the document's last node.

* scopes are **intervals over a (proper) suborder to the processing order**
* any super-order is order-preserving to all of its suborders
* any suborder is embedded into its super-order

Since the scope of a property follows the stream-based perspective (begins with
a defining node, ends with a last node, contains every other node in between),
each scope is a substring to the processing order. Because of that, base orders
must be such that the scopes over it are substrings to the processing order.

* any scope is a **substring** to the processing order
* the scopes over a base order must be substrings to the processing order

Note that one should not assume that any possible substring can be supported.
The above statements must therefore be understood to restrict what can be
supported (i.e. as **an upper boundary**). That is, further restrictions (i.e.
a refinment process) will be introduced.

<!-- ======================================================================= -->
## the trivial base order

Note that, due to having no edges at all, no nodes in the **trivial suborder**
of a document tree have any nodes subsequent to them. Any scope over a trivial
suborder therefore only consists of its defining node. Because of that, any
scope over the trivial base order is **a 1-element substring** to the
processing order.

* the trivial suborder of a processing order is a viable base order

<!-- ======================================================================= -->
## distinct and unqiue scopes

Recall that any scope is defined as an open interval over a base order that
begins with its defining node (i.e. a single node that is the scope's very
first node - i.e. a root). Based on that, any scope can insofar be described
as unique since each scope has a distinct starting point in regards to a
particular base order.

* all scopes over a base order must be **unique**

If there are two distinct nodes in a base order that have the same scope, then
that base order has a cycle. Both nodes could otherwise not have the same scope.
In addition to that, and since each node is then subsequent to the other, none
of the nodes has a characteristic element associated with it. That is because
the characteristic subset of that shared scope is empty.

* a base order must be **acyclic**

Note that any suborder to a tree order is acyclic by nature. Because of that,
and due to the overall context (i.e. document trees), this requirement can be
understood to be auto-satisfied.

Note that the scope over the last node of a processing order is equal to the
scope of that node over the trivial base order. Because of that, scopes can
not be required to be "globally unique".
