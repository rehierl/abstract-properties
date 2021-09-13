
<!-- ======================================================================= -->
## last nodes defined via sub-orders

Due to the above, an implementation can be said to **propagate a property
along the edges** of a pre-order trace. In other words, each property can be
understood to **emanate** from its defining node and to be **passed on to**
those nodes that are subsequent to it.

Since a pre-order trace can be seen as the union of sub-orders, each node in
a trace is the last node of one or more sub-orders (e.g. the rooted paths).
One can therefore in general define the last node of a property as the last
node of a well-defined sub-order since the last node of such a sub-order has
no outgoing edge (i.e. can be detected as such). Because of that, the last
node of a scope is a leaf to one or more sub-orders.

An implementation must be able to identify the corresponding sub-order as soon
as a defining node is reached. That is because an implementation must be able
to determine if the scope of a property contains more than its defining node.
After all, a defining node may in general be the first and also the last node
in the scope of a property.

The defining node of a property must therefore be a node in the corresponding
sub-order. Because of that, the last node of a property is, in regards to such
a sub-order, subsequent to the property's defining node (i.e. a valid path
must exist within the sub-order that connects both of these nodes). That is,
the last node of a property must be, according to the corresponding sub-order,
a descendant to the property's defining node.

In order to determine the appropriate sub-order given a property's defining
node, that node needs to be in a unique relationship with the sub-order. The
defining node of a property is therefore expected to be the first node in that
order. If that requirement is satisfied, then these orders are guaranteed to
be unique to each defining node. That is, no other defining node can have the
same sub-order(s) associated with it.

The sought-after sub-orders therefore need to begin with the defining node of
a property and they need to end with the last node in its scope. In addition
to that, these orders need to be substrings to a pre-order trace. The latter
is because, as stated above, the scope of a property needs to be continuous
in regards to a tree's pre-order trace.

Note that one could in general derive such sub-orders (e.g.) based on the
removal of those nodes in the rooted path of a defining node from some other
sub-order. The sought-after sub-orders could therefore be sub-orders to other
sub-orders. However, if there are sub-orders that can be determined with ease,
then there is no need for a sophisticated solution. After all, one would in
such a case, first have to derive the actual sub-order based on additional
processing steps (i.e. needlessly increased complexity).
