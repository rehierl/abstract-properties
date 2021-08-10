
<!-- ======================================================================= -->
# Generic properties

Note that the following definitions are meant to be of introductory nature.
That is, they provide a rough initial terminology. The definitions will then
be fleshed out based on the observable interaction between properties and
node orders.

```
n1 -> n2 -> n3 -> n4 -> d -> n6 -> n7 -> n8 -> n9
             <----------|----------->
           context   current    scope
```

A **defining node** `d` is such that it is understood to declare/introduce
some property `p`. The property a defining node declares can be understood
to represent a unique characteristic of some sort.

Note - Imagine that the property a defining node declares is some color which
is intended to to be used to "mark" all of the nodes within the property's scope.

In contrary to sectioning nodes and sections, each defining node may declare
one or more properties. However, each property is still associated with one and
only one defining node. Because of that, **a one-to-many relationship (1:n)**
exists between a defining node and the properties it declares.

Once the defining node of a property has been reached by an implementation, the
properties it declares are understood to apply to the defining node, and by
default to **all-of** those nodes that are subsequent to it. Because of that,
the **scope** of a property contains all of the nodes that are subsequent to
its defining node (`[d,*]`), in regards to the current node order.

Due to the above, each node within the scope of an abstract property can be said
to be associated with it. Consequently, an abstract property can be described as
being **shared across all of the nodes** within its scope.

* `d(p) := d` - the defining node of the specified property
* `s(p) := [d,*]` - the scope of the specified property

Any of the nodes that are presequent to the defining node `d` of a property
may themselves be defining nodes such that the defining node `d` is within
the scopes of the properties they declare. Based on that, these defining nodes
including the defining node `d` itself (`[*,d]`) are understood to form the
**context** of the defining node `d` and all of the properties it declares.

Due to the above **a scope is forwards oriented**. That is, a property can be
said to emanate from its defining node and to be propagated to all the nodes
that are subsequent to it. A property can therefore be said to "travel along
the edges". In contrary to that, **a context is backwards oriented**, against
the orientation of the edges, towards those nodes that are presequent. One
can therefore speak of **a forwards oriented, scope-based perspective** and
**a backwards oriented, context-based perspective**.

Note that, the terms "presequent" and "subsequent" can be said to have similar
orientation. That is, "presequent" is backwards oriented, while "subsequent"
is forwards oriented.

Note that, in regards to the orientation of the edges within a particular node
order, the scope of a property can be said to be consistent with the orientation
of that node order (i.e. "consistent" as in "same direction").

<!-- ======================================================================= -->
## why "abstract properties"?

Describing the above concept of properties as "abstract" is intended to reduce
confusion. That is because the description of a characteristic as a "property"
has, depending on a given context, various different meanings.

For example, the overall structure of the connections between vertices (e.g.
acyclic) can be described as a property of the corresponding relation (aka. a
graph property). Likewise, the concrete feature or characteristic of an object
(e.g. its weight) is in general also described as a "property".

In contrary to that, the use of the term "property" as described above is
intended to abstract the general process of marking all the elements (e.g.
with some color) that will be affected by an operation. As such, the type
of properties described can be understood as being purely abstract in nature.
Hence, the "abstract" qualifier.

However, and since these kind of properties can be understood to correspond
with scopes, they can in general be used to define the scopes of concrete
object properties. Based on that, one can speak of **generic scopes** and of
**types of scopes** instead of "abstract properties".
