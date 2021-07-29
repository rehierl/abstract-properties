
- requires scopes of multiple properties

any node may be
- the defining node of more than one property
- itself within the scopes of several other properties

<!-- ======================================================================= -->

scope => context
- a certain amount of duality
- a rule defined for a node and its descendants
- allows to make a statement in regards to the ancestors
- e.g. the definition of "context" is based on "scopes"
- scopes are forward oriented, a context is backwards oriented
- forwards vs. backwards - along/against the edges

context of a node
- in general the rooted path in an ordered tree
- i.e. if all the types of scopes are included/used
- can be restricted to the rooted path in an un-ordered tree
- if type-2/3 scopes are excluded
- i.e. restrict to `<section>` elements only
- i.e. don't use headings as sectioning nodes
- hence the need for transformations (i.e. hX => section)

a property can in general not end before the end of its scope
- i.e. can't in general exclude nodes from a scope
- whether a property is as an explicit/set property is secondary
- what counts is the existing path that begins in a defining node
- a node has a property, if it is connected to its defining node
- this is a structural definition can in general not be ignored

exceptions do exist
- t0 properties - e.g. id attribute (hint: descendants)
- t1 properties - e.g. hidden attribute (hint: siblings)
- rank-based headings and their sections

<!-- ======================================================================= -->

all sectioning nodes in the context of a node
- are on the rooted path in the ordered tree
- not just on the rooted path in the un-ordered tree
- it depeneds on the types of properties in use
- the issue is with headings

a node can not belong to a section whose sectioning node
- is not an ancestor in the rooted path in the ordered tree

<!-- ======================================================================= -->

no gaps
- if a node is marked with a property, then ...
- its descendants are related to that property
- i.e. test by walking up a rooted path
- note - the rooted path in an ordered tree!

the rooted paths in a tree are
- either related ex-or overlap each other
- i.e. "related" in terms of "super-/sub-string"
- "overlap" in that context has the role of "disjoint", not "related"
- i.e. "related" in terms of "super-/sub-set"
- i.e. an oriented vs. an un-oriented relationship

the rooted path of a node is a sub-sequence of a pre-order trace
- the rooted path of a section is a rooted path in the section hierarchy
- corresponds with a rooted path of sectioning nodes
- define a hierarchy of sectioning nodes
- define a prefix to a tree

a property exists in the context of a (sub-)tree
- i.e. restricted to the corresponding set of nodes

<!-- ======================================================================= -->
## un-ordered vs. ordered tree

rooted paths in un-ordered trees
- include ancestors only

rooted paths in ordered trees
- embed the rooted path in the un-ordered tree
- include the presequent siblings of a node
- include the presequent siblings of its ancestors

induced subtrees in un-ordered trees
- include descendants only

induced subtrees in ordered trees
- include descendants in the un-ordered tree
- the subsequent siblings of a node
- and their descendants
- but not the subsequent siblings of its ancestors

does the node order (i.e. the pre-order) force
- a section to include all the descendants?
- the pre-order trace of an ancestor is
  interleaved by the traces of its descendants
- the definition of a sub-section as a substring

<!-- ======================================================================= -->
## define context based on scopes

implications - seems to suggest
- the rooted path includes the context of a node
- the induced subtree includes those nodes
  on which a node may have an effect
- i.e. a heading may not have an effect on
  the subsequent siblings of an ancestor
  and their descendants

define the "context" of a node
- context := all the ancestors of a node
- i.e. all those on a rooted path

define the "scope" of a node
- i.e. its "area of effect"
- scope := all the descendants of a node
- i.e. the rooted path is a prefix

issue is with a trace
- i.e. the child order extends the set of ancestors and descendants
- likewise, the traversal rule can be said to do the same
- i.e. where to draw the line and why?
- why - a tree is not held in memory as a trace
  i.e. but as a tree (i.e. as connected nodes)
- if it comes to connected nodes, then what is
  the next node of a last sibling? difficult to find
- the next sibling of the nearest ancestor that has a next sibling
