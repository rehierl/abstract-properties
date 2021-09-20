
Recall that a property `p` is such that it is introduced by its defining node
`d` and understood to apply to all the nodes in its scope `s(d)`. Furthermore,
the scope of a property is such that it extends over its defining node and all
the nodes that are subsequent to it. Introduced as such, the scope of a property
suffers from the same issue as the section of a heading: The lack of a clear
definition of when it ends.

* `d(p) := d`, `s(p) := [d,*]`

However, since both concepts are based on defining nodes (e.g. a heading) which
introduce scopes, one can describe a section as the scope of a section property
and as such as an open interval over the appropriate **base order**. Because
of that, the concept of properties can be described as a generalization of the
concept of sections.

Note that the doctree's **pre-order trace** (aka. the document order,
**the processing order**) always is a viable base order. Likewise, and since
the first node of a scope may also be its last node, **the trivial suborder**
(i.e. the document's set of nodes combined with an empty set of edges) always
is an alternative base order.

Note that, from an even more generalized point of view, one can state that the
existence of an actual property is secondary. After all, what counts is that
there are certain nodes (i.e. the defining nodes) which introduce scopes as
intervals of over some base order.

This chapter will provide further insight into the inner workings of a doctree's
pre-order trace, with the intent of listing those orders that are embedded into
it.
