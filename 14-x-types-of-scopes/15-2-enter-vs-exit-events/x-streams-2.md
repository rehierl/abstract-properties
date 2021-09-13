
<!-- ======================================================================= -->
## a stream-based perspective

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 )
 |-prefix---||-infix/scope--||-suffix----|
```

Since a property is required to be continuous, a property can be understood to
define three disjoint substrings in the pre-order trace of a tree: (1) a prefix
which does not contain any node in the property's scope, (2) a non-empty infix
(i.e. the property's scope), and (3) a suffix which, like the prefix, does not
contain any node in the property's scope. (Note that, the prefix and the suffix
may both be empty). Because of that, and in regards to a property, the trace of
a tree can be understood to be formed by concatenating these substrings (i.e.
`t := (prefix × scope × suffix)`).

Since the pre-order trace is an ordered sequence of nodes, the prefix and the
suffix of a trace in regards to a property can also be understood to be defined
by a property's scope. That is, given the pre-order trace of a tree and the
scope of a property, one can determine the corresponding prefix and suffix.

Also, and since the scope of a property is non-empty, all three substrings can
be visualized by **underlining all the nodes in a scope**.

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 )  | a pre-order trace,
             ================                | the scope of property 'p'
                                             |
 |-prefix---||-scope--------||-suffix----|   | scope = area-of-effect (AOE)
 |-unknown--||-defined-------------------|   |
                                             |
s(p) := [n4,n7] := ( n4, n5, n6, n7 )        | visualized definitions
N(p) := E(s(p)) := { n4, n5, n6, n7 }        |
prefix := [n1,n3], suffix := [n8,n10]        |
```

While visiting the nodes that are presequent to a property's defining node,
the property counts as being **undefined** to an implementation. However,
as soon as the defining node of a property is reached, the property counts
as being **defined**, which is why an implementation needs to create an
internal object it can use to associate all the nodes within the scope.

Note that the first node of a property obviously needs to have characteristics
which allow an implementation to identify it as the defining node of a property.
This however is easily done by (e.g.) simply specifying the property via an
attribute of the corresponding node.

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 )
 |-unknown--||-scope/open---||-closed----|
```

The initialization will obviously have to mark the property as being **open**
for associations and set the property as a property of the property's defining
node. From that point on, an implementation can associate the property with
each subsequent node for as long as the property counts as being open. And
since a property has a last node, even if that node is the last node of the
pre-order trace, an implementation must mark a property as being **closed**
once the property's last node is reached and associated. This closed state
informs an implementation that the corresponding property is "done". Because
of that, an implementation is no longer allowed to associate the property
with further subsequent nodes.

Note that it is in general secondary to the overall result in which order the
nodes of a scope are associated. That is, the information when exactly a node
was associated will not be saved (i.e. that information will be lost). Because
of that, an implementation may in general associate node `n6` right after `n4`
and therefore even before `n5`. However, since a scope is required to be
continuous, `n5` must still be associated at some point.

Note that these processing steps will in general be referred to as
**the stream-based perspective** of an implementation on a property.

If the pre-order trace of a tree is processed as described above, then an
implementation can in general determine for each node whether or not that
node is within a property's scope. All an implementation needs to do is to
verify that the property is set as a property of the corresponding node.

In contrary to that, there is up to this point no description of how an
implementation can identify the last node of a property. That is, generic
definitions are required which allow to reliably determine when the end
of a scope was reached.

Note that, since the defining node of a property is an element in its scope,
the scope of a property can be said to be defined as an interval whose lower
bound (i.e. a defining node) is included (i.e. thus far `s(p) := t[first,?`).
