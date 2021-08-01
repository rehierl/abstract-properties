
<!-- ======================================================================= -->
# Generic properties

Note that the following definitions are meant to be introductory. That is,
they provide an initial rough terminology. The definitions will be fleshed
out based on the observable interactions between properties and node orders.

```
n1 -> n2 -> n3 -> n4 -> d -> n6 -> n7 -> n8 -> n9
             <----------|----------->
           context   current    scope
```

A **defining node** `d` is such that it is understood to declare/introduce a
some property `p`. The property a defining node declares can be understood to
represent a unique characteristic of some sort (e.g. a color).

In contrary to sectioning nodes and sections, each defining node may declare
one or more properties. However, each property is still assocated with one
defining node only. Because of that, **a one-to-many relationship (1:n)**
exists between the defining nodes and the properties they declare.

Once the defining node of a property has been reached, the properties it
declares are understood to apply to the defining node itself, and to **all-of**
those nodes that are subsequent to it (i.e. `[d,*)`). Based on that, the nodes
to which a property applies are said to be within the **scope** of the defining
node and all of the properties it declares.

* `d(p) := d`
* `s(d), s(p) := [d(p),*)`

Any of the nodes that are presequent to the defining node `d` of a property
may themselves be defining nodes such that the defining node `d` is within
their scopes. Based on that, the defining nodes that are presequent to the
defining node `d`, including the defining node itself (i.e. `(*,d]`) can be
understood to form the **context** of the defining node `d` and all of the
properties it declares.

Due to the above **a scope is forwards oriented**. That is, a property can be
said to emanate from its defining node and to be propagated to all the nodes
that are subsequent to it. A property can therefore be said to "travel along
the edges", which is consistent with the underlying node order. In contrary
to that, **a context is backwards oriented**. One can therefore speak of
**a forward/scope-based**, and **a backward/context-based perspective**.

The concept of "scopes" can therefore be said to represent a forwards oriented
perspective, along the orientation of the edges towarads those nodes that are
**subsequent**. In contrary to that, the concept of "context" can be said to
represent a backwards oriented perspective, against the orientation of the
edges, towards those nodes that are **presequent**. Based on that, the terms
presequent/subsequent can be said to have similar orientation.

<!-- ======================================================================= -->
## why "generic properties"?

Describing the following concept of properties as "generic" is intended to
reduce confusion. That is because the description of a characteristic as a
"property" has, depending on a given context, various different meanings.

For example, the overall structure of the connections between vertices (e.g.
acyclic) can be described as a property of the corresponding relation (i.e. a
graph property). Likewise, the concrete feature or characteristic of an object
(e.g. its weight) is in general also described as a "property".

In contrary to that, the use of the term "property" as described below abstracts
the general process of marking all the elements (e.g. with some color) that will
be affected by an operation. As such, the type of properties as described below
can be understood as being purely abstract in nature.

However, and since these kind of properties can be understood to correspond with
scopes, they can in general be used to define concrete object properties and the
scopes of operations. Based on that, one could also speak of **generic scopes**
or of **types of scopes** rather than of "generic properties".
