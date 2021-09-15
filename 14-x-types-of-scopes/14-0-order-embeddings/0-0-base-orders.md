
Recall that an abstract property `p` is such that it is introduced by its
defining node `d` and understood to apply to all the nodes in its scope `s(d)`.
Furthermore, the scope of a property is such that it extends over its defining
node and all the nodes that are subsequent to it. A property's scope can thus
be described as **an open interval over some known base order**.

* `d(p) := d`, `s(p) := [d,*]`

Introduced as such, the scope of an abstract property suffers from the same
issue as the section of a heading: The lack of a clear definition of where
it ends.

However, since both concepts are based on defining nodes (e.g. a heading)
that introduce scopes, one can describe a section as the scope of an abstract
(section) property. Because of that, the concept of properties can be described
as an abstraction of the section concept.

Note that, from an even more generalized point of view, one could state that
the existence of an actual property is secondary. After all, what counts is
that there are certain nodes (i.e. defining nodes) which introduce scopes of
some sort.

This chapter will provide further insight into the inner workings of a doctree's
pre-order trace, with the intent of listing those orders that are embedded into
it, and in an attempt to answer the following question:

* A scope is an interval over which base order?

Note that one will eventually have to answer the following question: To which
scopes does a given node belong? To answer that question a clear understanding
of all the node orders that are involved is essential.
