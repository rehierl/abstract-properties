
<!-- ======================================================================= -->
## remarks

Note that, although it is obvious from the definition, the concept of generic
properties is closely related to intervals. Put differently, generic properties
can be understood as an application that is based upon one particular type of
intervals: those that are unrestricted to the right hand side (i.e. `[x,*)`).

Note that generic properties, as an application of "Order Theory", represent
a low-level layer of abstraction. As such generic properties can be said to
represent the foundation of a bottom-up approach.

Note that the **fluid dynamics** of a river, which is flowing down a hill (e.g.
a waterfall), seems to be a decent analogy. Just as water is forced by gravity
to flow downhill, the scope of a generic property can be understood to be
forced/pushed by the underlying node order to travel along the edges. Similar
to that, one can think of water flowing down a drain/pipes.

Note that the property of a defining node can be described as a property that
is **shared** among all the nodes within its scope. Put differently, the nodes
within a scope can be said to be associated with the same property.

Note that, an object that is intended to represent a property can be created
with each defining node. In addition to that, the object can be associated with
the defining node and marked as being open for associations. Once there are no
more nodes subsequent to the defining node, the object created can be marked as
being closed. Based on that, generic properties can be understood to support
**a stream-based perspective** and to be consistent with the
**past-present-future analogy**.

Note that, since each node may be within the scopes of one or more properties,
and since each property may apply to one or more nodes, there is a
**a many-to-many relationship (n:m)** between the set of all the properties
within a document and the set of nodes in it.

Note that the definition of "context" is based upon the definition of "scope".
Because of that, **"context" is a consequence of "scopes"**. Consequently,
and in order to allow to uniquely determine the context of each node within
a document, one first needs to unambiguously define the scopes of all the
properties that are allowed within a document.

Note that "all of the subsequent nodes included" is at this point a mere
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
