
<!-- ======================================================================= -->
## remarks

Note that, although it is obvious from the definition, the concept of abstract
properties is **closely related to intervals**. Put differently, abstract
properties can be understood as an application of the concept of intervals.
And since each interval can be understood to define an ordered subset, abstract
properties can be described as an application of Order Theory.

Note that abstract properties represent a low-level layer of abstraction. As
such abstract properties can be described to represent the foundation of a
bottom-up approach.

Note that, an object that is intended to represent a property can be created
with each defining node. In addition to that, the object can be associated with
the defining node and marked as being open for associations. Once there are no
more nodes subsequent to the defining node, the object created can be marked as
being closed. Based on that, abstract properties can be understood to support
**a stream-based perspective**.

Note that, since each node may be within the scopes of multiple properties,
and since each property may apply to one or more nodes, there is a
**a many-to-many relationship (n:m)** between the set of all the properties
within a document and the set of nodes in it.

Note that **"context" is a consequence of "scopes"**. That is, the definition
of "context" is based upon the definition of "scope". Because of that, and in
order to allow to uniquely determine the context of each node within a document,
one first needs to unambiguously define the scopes of all the properties that
can be used within a document.

<!-- ======================================================================= -->
## analogies

Note that the concept of abstract properties is consistent with the
**past-present-future analogy**.

Note that the **fluid dynamics** of a river, which is flowing down a hill (e.g.
a waterfall), seems to be a decent analogy. Just as water is forced by gravity
to flow downhill, an abstract property can be understood to be forced/pushed
by the underlying node order to travel along the edges. Similar to that, one
can think of water flowing down a drain/pipe.

<!-- ======================================================================= -->
## possible extensions

Note that "all of the subsequent nodes included" counts at this point as an
"initial assumption". That is, the above definition of scope must be understood
to define the default scope of a property. Put differently, it may still be
possible to support additional rules (i.e. **extensions**, e.g. rank values)
that can be used to prematurely end the default scope of a property.

Note that, any node subsequent to a defining node is said to be within the
scopes of all the properties the defining node declares. Based on that one
can in principle not negate/ignore this **structural relationship**. Clear
rules will therefore be requried in order to "bend the rules" such that,
prematurely closing the default scope of a property can be supported. Once
again, the "some-of" qualifier is the issue.
