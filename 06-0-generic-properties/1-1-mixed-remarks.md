
<!-- ======================================================================= -->
## remarks

Note that, although it is obvious from the definition, the concept of generic
properties is closely related to intervals. Put differently, generic properties
can be understood as an application that is based upon one particular type of
intervals: those that are unrestricted to the right hand side (i.e. `[d,*]`).
As such, generic properties can be described as an application of Order Theory.

Note that generic properties represent a low-level layer of abstraction.
As such generic properties can be described to represent the foundation
of a bottom-up approach.

Note that the **fluid dynamics** of a river, which is flowing down a hill (e.g.
a waterfall), seems to be a decent analogy. Just as water is forced by gravity
to flow downhill, the scope of a generic property can be understood to be
forced/pushed by the underlying node order to travel along the edges. Similar
to that, one can think of water flowing down a drain/pipe.

Note that the property of a defining node can be described as a property that
is **shared** among all of the nodes within its scope. Put differently, the
nodes within a scope can be said to be associated with the same property.

Note that, an object that is intended to represent a property can be created
with each defining node. In addition to that, the object can be associated with
the defining node and marked as being open for associations. Once there are no
more nodes subsequent to the defining node, the object created can be marked as
being closed. Based on that, generic properties can be understood to support
**a stream-based perspective** and to be consistent with the
**past-present-future analogy**.

Note that, since each node may be within the scopes of multiple shared
properties, and since each property may apply to one or more nodes, there is
a **a many-to-many relationship (n:m)** between the set of all the properties
within a document and the set of nodes in it.

Note that the definition of "context" is based upon the definition of "scope".
Consequently, **"context" is a consequence of "scopes"**. Because of that,
and in order to allow to uniquely determine the context of each node within
a document, one first needs to unambiguously define the scopes of all the
properties that can be used within a document.

Note that, any node subsequent to a defining node is said to be within the
scopes of all the properties that defining node introduces. Based on that
one can in principle not negate/ignore this **structural relationship**.
Clear rules will therefore be requried in order to "bend the rules" such
that, prematurely closing the default scope of a property can be supported.
Once again, the "some-of" qualifier is the issue.

Note that "all of the subsequent nodes included" is at this point a mere
"initial assumption". That is, the above definition of scope must be understood
to define the default scope of a property. Put differently, it may still be
possible to support additional rules (i.e. **extensions**, e.g. rank values)
that can be used to prematurely end the default scope of a property.
