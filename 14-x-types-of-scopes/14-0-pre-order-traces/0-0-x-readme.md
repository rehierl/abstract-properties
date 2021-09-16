
Recall that a property `p` is such that it is introduced by its defining node
`d` and understood to apply to all the nodes in its scope `s(d)`. Furthermore,
the scope of a property is such that it extends over its defining node and all
the nodes that are subsequent to it. A property's scope can thus be described
as **an open interval over some base order**, one of which is the doctree's
**pre-order trace** (aka. a doctree's **processing order**).

* `d(p) := d`, `s(p) := [d,*]`

Note that, since a defining node may in general be the first and also the last
node in a scope, the **trivial suborder** (i.e. the document's set of nodes
and an empty set of edges) is a possible alternative base order.

Introduced as such, the scope of a property suffers from the same issue as the
section of a heading: The lack of a clear definition of where/when it ends.

However, since both concepts are based on defining nodes (e.g. a heading) which
introduce scopes, one can describe a section as the scope of a section property.
Because of that, the concept of properties can be described as an abstraction
of the concept of sections.

Note that, from an even more generalized point of view, one could state that
the existence of an actual property is secondary. After all, what counts is
that there are certain nodes (i.e. defining nodes) which introduce scopes as
intervals of over some known order.

This chapter will provide further insight into the inner workings of a doctree's
pre-order trace, with the intent of listing those orders that are embedded into
it, which will be required to answer the following question:

* A scope is an interval over which base order?
