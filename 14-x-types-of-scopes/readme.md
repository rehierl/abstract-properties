
# types of scopes

Recall that a property `p` is such that it is introduced by its defining node
`d(p)` and understood to apply to the nodes in its scope `s(d)`. Furthermore,
the scope of a property is such that it extends over its defining node and the
nodes that are subsequent to it. Introduced as such, the scope of a property
suffers from the same issue as the section of a heading: The lack of a clear
definition of when it ends.

* `d(p) := d` - the defining node of a property `p`
* `s(p) := [d,*]` - the scope of a property

However, since both concepts are based on defining nodes (e.g. a heading)
which introduce scopes, a section can be understood as the scope of a section
property and can as such be described as an open interval over the corresponding
**base order**. Based on that, the concept of properties can be understood as
**a generalization of the concept of sections**.

Note that the doctree's **pre-order trace** (aka. the document order, aka.
its **processing order**) is always a viable base order. Likewise, and since
the first node of a scope may also be its last node, **the trivial suborder**
(i.e. the document's set of nodes but with an empty set of edges) is always
an alternative base order.

Note that, from an even more generalized point of view, one can state that the
existence of an actual property is secondary. After all, what counts is that
there are certain nodes (i.e. the defining nodes) which introduce scopes as
intervals over the corresponding base order.
