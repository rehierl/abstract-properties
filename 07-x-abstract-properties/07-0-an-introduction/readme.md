
# abstract properties / an introduction

The following provides an introduction to the concept of abstract properties,
which can be understood to generalize the concept of sections.

Note that the term "property" must in this context be understood to refer to
**a characteristic of some kind** - e.g. a group identifier or some color.

Like sections, no property applies to those nodes that are presequent to its
defining node. In other words, each property may only affect its defining node,
and all those nodes that are subsequent to it. That is, the **scope** of any
property is forwards oriented, along the edges of the corresponding node order.

Note that the document order is defined as the pre-order trace of a document
tree. Based on that, each node has a **unique index** associated with it, which
can be understood to provide **an initial definition of** what is **presequent**
and what is **subsequent**. However, one needs to be aware that both definitions
is **strictly speaking based on suborders to the document order**. The document
order is merely order-preserving in regards to these suborders.

Note that this abstract concept of properties can even be used to define the
scope of **operations**. That is because, one can think of an operation as
first pre-selecting all the nodes that will be affacted by the operation by
marking the corresponding nodes using some unique property (e.g. a group id).
After that, the operation can be executed on the pre-selected nodes.

As with sections, the difficulty when defining the scope of a property is to
clearly define which of the nodes that are subsequent to a defining node are
affected by a property (i.e. within the property's scope), and which ones
are not. It is straight forward, if **all-of** or **none-of** the nodes are
included since these **quantifiers** are easy to implement. However, it is
not so clear if **some-of**, but not all of the nodes are included.

Since a some-of quantifier can in principle be defined in terms of an "all of
the nodes up to a certain point, but none after that" **restriction**, one
still has the difficulty of having to define the point of transition. That is,
one must still clearly **define the end** of the property's scope.

* some-of := (all-of + none-of)

As a starting point an abstract property `p` is understood to apply to all of
the nodes that are subsequent to its defining node `d`. That is, the default
scope of a property `s(p)` can be described as **an open interval** over the
corresponding node order.

* `d(p) := d` - the property's defining node
* `s(p) := [d,*]` - the property's (default) scope

Note that such an open interval does not directly specify the end of the
property's scope. That is, the last node within the scope of a property
must be determined based on the underlying node order.

Note that the scope of a property is **forwards oriented** - i.e. oriented
with the edges of the corresponding node order. In contrary to that, the
**context** of a property is **backwards oriented** against the node order.
