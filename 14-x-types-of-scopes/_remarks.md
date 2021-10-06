
rank-based sections
- use the total document order to introduce rank-based sections
- i.e. translate the tag-based syntax into a rank-based syntax
- i.e. associate a rank/depth value with each node
- allows to explain how a node order can be broken apart

context rooted paths
- the last node of a property is subsequent to its
  defining node, because of that, the defining node
  is a node in the last node's rooted path
- a matter of consequence

# implementations

a stack of stacks of open scopes
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

# general / meta

general impression
- we are overly used to total orders
- we are barely aware of partial orders
