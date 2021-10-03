
html headings
- introduce the h-element as a DTO scoped heading?
- i.e. and leave the others as broken DPR headings?
- no - that would result in a mess of scopes
- otherwise, the inconsistency in scopes issue remains
- all headings must be DTO headings
- and the h-element is the only rank-less heading

allowing to prematurely close a scope
- by the descendant of an associated container
- can break the stream-based pov by introducing gaps
- will break grouping by tags

dom tree - order embedding
- point out the implementation-specific aspects of a dom tree
- point out that DTR, DTU and DTO are embedded suborders
- pout out that DPR is no embedded suborder

# next todo

rank-based sections
- use the total document order to introduce rank-based sections
- allows to explain how a node order can be broken apart

context rooted paths
- the last node of a property is subsequent to its
  defining node, because of that, the defining node
  is a node in the last node's rooted path
- a matter of consequence

# extensions

# implementations

- a stack of stacks of open scopes

# general / meta

general impression
- we are overly used to total orders
- we are barely aware of partial orders
