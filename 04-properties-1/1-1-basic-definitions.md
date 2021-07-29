
<!-- ======================================================================= -->
# Generic properties

```
- n1 - n2 - n3 - n4 - d - n6 - n7 - n8 - n9 ->
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
## remarks

Note that the **fluid dynamics** of a river, which is flowing down a hill (e.g.
a waterfall), seems to be a decent analogy. Just as water is forced by gravity
to flow downhill, the scope of a generic property can be understood to be
forced/pushed by the underlying node order to travel along the edges.

Note that the overall context of this discussion is on ordered sequences
and that a scope is defined to begin with a defining node, and also defined
to contain all the other nodes that are subsequent to it. Based on that, the
scope of a property can be described **as an (open) interval** (i.e. `[d,*)`)
over the corresponding node order. Put differently, the scope of a property
can be described **as a suffix** over the underlying node order.

Note that each interval defines an ordered set of elements. Because of that,
any scope can be understood to correspond with **an ordered (sub)set of nodes**.

Note that the property of a defining node can be described as a property that
is **shared** among all the nodes within its scope. Put differently, the nodes
within a scope can be said to be associated with the same property.

Note that, an object that is intended to represent a property can be created
with each defining node. In addition to that, the object can be associated with
the defining node and marked as being open for further associations. Once there
are no more nodes subsequent to the defining node, the object created can be
marked as being closed. Based on that, generic properties can be understood
to support **a stream-based perspective** and to be consistent with the
**past-present-future analogy**.

Note that, since each node may be within the scopes of one or more properties,
and since eac property may apply to one or more nodes, there is a
**a many-to-many relationship (n:m)** between the set of all the properties
within a document and its set of nodes.

Note that the definition of "context" is based upon the definition of "scope".
Because of that, **"context" is a consequence of "scopes"**. Consequently,
and in order to allow to uniquely determine the context of each node within
a document, one first needs to unambiguously define the scopes of all the
properties that can be used within a document.

Note that "all of the subsequent nodes included" is at this point an mere
"initial assumption". That is, the above definition of scope must be
understood to define the **default scope** of a property. Put differently,
it may still be possible to support additional rules (e.g. rank values) that
can be used to prematurely end the default scope of a property.

Note that, any node subsequent to a defining node is said to be within the
scopes of all the properties that defining node introduces. Based on that
on can in principle not negate/ignore this **structural relationship**.
Clear rules will therefore be requried in order to "bend the rules" such
that, prematurely closing the default scope of a property can be supported.
Once again, the "some-of" qualifier is the issue.
