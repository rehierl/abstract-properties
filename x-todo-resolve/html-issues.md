
- this repository is about the concept of generic
  properties and as such a purely theoretical discussion
- a summary/discussion of core/fundamental aspects
  in regards to html's core issues
- extract into its own repository since this is
  almost guaranteed to grow ways past the scope
  of this repository

# the tag-based syntax

- visually derive the tag-based syntax
- i.e. push a node into its start-tag
- the document order is the doctree's pre-order trace

a tag soup ain't no (fucking) node tree
- derive the family of scopes from a tag soup
- the tag-based syntax is an application of generic
  properties, which is an application of order theory

the some-but-not-all qualifier
- an end-tag separates a node's type-1 (t1) descendants
  from its remaining t2 descendants - i.e. from the
  subsequent siblings and their t1 descendants
- or - from the next subsequent sibling and its t2 descendants
- as such, an end-tag provides a clear definition
  for the some-but-not-all case/qualifier
- a partition of its type-2 descendants

has consequences in regards to ..
- the start-/end-tags
- each node corresponds with its start-tag
- a node's end-tag marks the end of
  the node's type-1 scope - nothing more
- "visiting a node" in general only corresponds
  with processing the node's start-tag
- the enter/exit order as an order of events
- "entering and exiting node"

# the dom "tree"

- point out the implementation-specific
  aspects of a dom tree
- explain why the tree orders can still be said
  to be sub-orders to that non-tree graph

# parent div containers

a parent div container
- not within the scope of a section that
  is declared by a descendant heading
- the h1-div-h1 fragment/issue

an inconsistency in scopes
- point out the "inconsistency in scopes" issue
- using the "hidden" attribute

# rank values, an extension

rank values in general (?)
- can be supported
- explain using set-/intervall-based operations
- always in regards to some context
- rank values are not absolut
