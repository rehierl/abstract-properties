
<!-- ======================================================================= -->
# base order candidates

Recall that a doctree's pre-order trace (aka. **the processing order**), is
the node order in which a document tree must be processed. That is because
there needs to be a total order over all the nodes in a document such that
distinct implementations can be guaranteed to produce the exact same result.

* a tag soup encodes the processing order
* a tag soup allows to visualize the processing order

Note that definitions in regards to a tag soup are therefore not in regards
to the tag-based syntax (i.e. some specific syntax), but in regards to the
processing order and the suborders it embeds.

Recall that each scope is defined as an open interval (i.e. an induced suborder)
such that it begins with its defining node and includes every other node that
is subsequent to it. Even though the processing order may be used as a base
order, the following tries to focus on finding restrictions all base order
candidates must satisfy.

* the processing order is a base order candidate
* any base order is a (proper) suborder to the processing order

Since any scope over the processing order will end in the document's last node,
any alternative base order is in general such that the scopes over it will end
before the document's last node.

* scopes are **intervals over a (proper) suborder to the processing order**
* any super-order is order-preserving to its suborders
* any suborder is embedded into its super-order

Since the scope of a property follows the stream-based perspective (begins with
a defining node, ends with a last node, contains every other node in between),
each scope is a substring to the processing order. Because of that, base orders
must be such that the scopes over it are substrings to the processing order.

* any scope is a **substring** to the processing order
* the scopes over a base order must be substrings to the processing order

Note that one should not assume that any substring can be supported. The above
statements must therefore be understood to restrict what can be supported (i.e.
as **an upper boundary**). That is, further restrictions (i.e. a refinment
process) will be introduced.

<!-- ======================================================================= -->
## trivial base orders

Note that, due to having no edges at all, there is no node in the doctree's
**trivial suborder** that has another node subsequent to it. Any scope over
a trivial suborder therefore only consists of its defining node. Because of
that, any scope over the trivial base order is **a 1-element substring** to
the processing order.

* the trivial suborder of a processing order is a viable base order
* aka. **the trivial base order**

<!-- ======================================================================= -->
## distinct and unqiue scopes

Recall that any scope is defined as an open interval over a base order that
begins with its defining node (i.e. a single node that is intended to be the
scope's very first node - i.e. a root). Based on that, any scope can insofar
be described as unique since each scope then has a distinct starting point
in regards to a particular base order.

* the scopes over a base order are expected to be **unique**

Note that "expected to be" in this context must be understood as a requirement
for which there is (thus far) no proof that would turn it into an absolute
necessity.

The node of a cycle should not be used as the root of a scope since such a
node is subsequent to itself. That is, there is no real starting point to a
cycle. Consequently, and since (from the perspective of generic definitions)
any node can potentially be used as the defining node of a scope, base orders
are expected to be acyclic.

* a base order is expected to be **acyclic**

Note that any suborder to a tree order is acyclic by nature. Because of that,
and due to the overall context (i.e. document trees), this requirement can be
understood to be auto-satisfied.

Note that the scope over the last node of a processing order is equal to the
scope of that node over the trivial base order. Because of that, scopes can
not be required to be "globally unique".
