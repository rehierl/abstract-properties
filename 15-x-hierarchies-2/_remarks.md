
# implementations

proof-of-concept (poc) implementations
- implementations to show that this isn't fictional

implementations
- a stack of stacks of open scopes
- relevant with hierarchies of sections
- a stack-of-stacks is consistent with the closing order
- if exit-events of multiple scopes match the same end-tag?
- hint - last opened, first closed - a consequence of DI-RE

# topics - next

rank-based scopes
- use the total document order to introduce rank-based sections
- i.e. translate the tag-based syntax into a rank-based syntax
- i.e. associate a rank/level value with each node
- allows to explain how a node order can be broken apart

# topics - next-2

- relationships between scopes
- scopes of multiple properties
- not much of an issue if scopes are related
- an issue if scopes overlap - inconsistent scopes

What does it mean if the to-be-removed node has a characteristic that is
considered to also apply to its descendants (e.g. a specific color)?

After all, once that node was removed, such a characteristic can no longer
apply to its former descendants since the defining node of that characteristic
was removed. The removal of a node may therefore have unintended side effects,
if the operation is restricted to a single node.

# topics - context

context rooted paths
- the last node of a property is subsequent to its defining node
- the defining node is a node in the last node's rooted path
- a matter of consequence
