
scopes amount to nodes
- scopes of nodes amount to sections
  by selecting a subset of scopes
- sections amount to outlines
- outlines amount to outline hierarchies
  by selecting a subsets of sections

can be used to explain
- abstract properties based on fluid dynamics
- an introduction to hierarchies

sequences
- don't focus on the elements in each component
- each component has its own unqiue index
- the indexes allow to identify the elements
- a sequence corresponds with a set of distinct elements
- as such corresponds with an ordered set

side scrolling games
- then - height diffs of +1d/-1d at a time - node hierarchy
- then - height diffs of +1d/-n*d at a time - section hierarchy
- issue - gaps in height - i.e. +n*d - not possible
  one new section per sectioning node
- issue - gaps in width - not supported - no canyons, no gorges

# initially, focus on monotone increasing paths

paths are considered to be monotone
- plus one ex-or minus one overall
- overall montone increasing/decreasing

assume monotone increasing
- since all layers have the same discrete height h
- (+1*h) with each step/increase
- add up all heights, you get a node level

# height map, node levels

in regards to borders
- if at a current layer and at an overall level of (n)
- if that layer ends, then that does not mean a remaining height
  of (n-1) - i.e. not a total value minus a discrete change
- it means that the former layer's (+1) is no longer applicable
- i.e. add up all remaining heights - i.e. (+1)*(n-1),
  i.e. the discrete height of each layer multiplied by the
  number of remaining layers - i.e. those that still count
- you don't subtract what no longer exists,
  you add up what still exists
- the difference is subtle but essential

in regards to properties
- the corresponding path has ended
- the information defined on it is no longer relevant
- don't focus on what no longer is
- foucs on what is truly defined,

partial orders
- similar to in-comparable elements
- they tend to be irritating due to the lack of definition
- but that is not what you should be focussing on
