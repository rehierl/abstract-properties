
- this is about abstract properties
- there are no actual implementations
- i.e. a purely theoretical discussion

# topics - meta

- an outline of an outline

overall impression
- we are overly used to total orders
- we are barely aware of partial orders

# topics - rank values

a rank-based heading
- is a descendant to a presequent heading over DPR
- a heading acts like a `<section>` element over DTO

howto see rank values
- set the rank value of each sectioning node to its node level
- rescale all rank values such that they only increase by +1
- issue with - headings that have the same parent

# topics - beyond

html headings
- introduce the h-element as a DTO scoped heading?
- i.e. and leave the others as broken DPR headings?
- no - that would result in a mess of scopes
- otherwise, the inconsistency in scopes issue remains
- all headings must be DTO headings
- and the h-element is the only rank-less heading

allow to prematurely close a scope
- by the descendant of an associated container
- will break the stream-based perspective by introducing gaps
- a descendant heading (as t3) can not close the section of
  a heading with which its ancestor container is associated
- the descendant heading is restricted to the container
- will also break grouping-by-tags

any node can be understood to have an outline
- think in terms of the type-1 scope of a node
- i.e. allows to treat any node as the starting point
- issue header element in combination with reusing heading elements
- i.e. a 1st header element can not always be recognized to be with
  regards to a presequent type-1 sectioning node
- possibly outside of corresponding subtree
- an implementation-specific issue - in regards to producing
  an outline based on any given input node - not just the root
- an algorithm can in principle start at any node
- a root must be treated as a type-1 sectioning node
- could that type-switching even be implemented?
- sure - detect if exiting at node level 1

given a set of nodes N
- what is the max number of possible hierarchies?
- recall - the css of a leaf reduces N by #css,
  and thus the number of possible parent sets
- does this allow a recursive calculation?
- in regards to - resource/memory management
- most likely too large to be relevant
