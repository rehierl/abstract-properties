
now that the pre-order trace is known
- can show the remaining hierarchies
- a hierarchy of pre-order sub-traces,
  just another hierarchy of scopes
- length values in pre-order
- levels from rooted paths in pre-order

rank-based sections
- use the total document order to introduce rank-based sections
- i.e. translate the tag-based syntax into a rank-based syntax
- i.e. associate a rank/depth value with each node
- allows to explain how a node order can be broken apart

# general / meta

- an outline of an outline

general impression
- we are overly used to total orders
- we are barely aware of partial orders

# next-level

relationships between scopes
- relevant if it comes to scopes of multiple properties
- not much of an issue if scopes are related
- an issue if scopes overlap - inconsistent scopes

What does it mean if the to-be-removed node has a characteristic that is
considered to also apply to its descendants (e.g. a specific color)?

After all, once that node was removed, such a characteristic can no longer
apply to its former descendants since the defining node of that characteristic
was removed. The removal of a node may therefore have unintended side effects,
if the operation is restricted to a single node.

# context

context rooted paths
- the last node of a property is subsequent to its
  defining node, because of that, the defining node
  is a node in the last node's rooted path
- a matter of consequence

# implementations

a stack of stacks of open scopes
- relevant with hierarchies of sections
- a stack-of-stacks is consistent with the closing order
- if exit-events of multiple scopes match the same end-tag?
- hint - last opened, first closed

# extensions

html headings
- introduce the h-element as a DTO scoped heading?
- i.e. and leave the others as broken DPR headings?
- no - that would result in a mess of scopes
- otherwise, the inconsistency in scopes issue remains
- all headings must be DTO headings
- and the h-element is the only rank-less heading

allowing to prematurely close a scope
- by the descendant of an associated container
- will break the stream-based perspective by introducing gaps
- a descendant heading (as t3) can not close the section of
  a heading with which its ancestor container is associated
- the descendant heading is restricted to the container
- will also break grouping-by-tags

a rank-based heading
- is a descendant to a presequent heading in the DPR
- acts like a `<section>` element in regards to the DTU
