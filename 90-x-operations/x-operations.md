
Once an implementation has determined the relationships of a node with the
sections in a document, one would want to use the additional information to
fold the contents of a section. In general, such operations are implemented
based on hiding, or by simply skipping the affected nodes.

At the very core of each operation is however the knowledge of all the nodes
that are included. That is, implementations need a clear definition of the
group of nodes for which an operation is to be executed (e.g. one of the
scopes of the operation's defining/first node).

From a theoretical perspective, implementations can therefore be understood
to preselect all the nodes before executing an operation. That is, one can
assume that an implementation first begins to tag all the nodes in a scope
with a unique property.

Note that, in the context of this discussion, one can think of a property as
some unique id/reference which states that the tagged node is located within
a given scope. As such, the **some-of** qualifier can be said to be replaced
by an **all-of** qualifier. Based on that, each defining node of a scope can
be described as the defining node of a property.

Note that, in subsequent discussions it will be the other way around. That
is, the definition of a property will be associated with a particular type of
scope. As such, a property is in general defined to apply to all the nodes an
implementation will reach while traversing through the property's scope.
