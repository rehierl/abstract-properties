
# when to associate (2)

* recall that a document is processed as a node tree,
  that is where properties/attributes take effect,
  properties, except for the tags themselves are
  dead meat/weight in the context of a tag soup

when focussing on scopes of nodes only

* the case is easy - either "all in exor none at all",
  a consequence, not exactly an aboslute necessity
* that is a consequence of the tag-based syntax - a containment order
* the scope of a node automatically extends over all the descendants
* hint - mark a node as hidden - will hide all its descendants
* easier to implement that way - if the hidden attribute is set,
  then skip/ignore all the descendants of that node
* a consequence - a defining node is within the rooted path - context

future extensions

* may possibly close the scope of a node?
* type-2 is not "the scope of a node"
* type-2 refers to an extended scope
* the extended scope of a child
* same issues with distant descendants
* type-3 - an unrestricted scope

In regards to the extended scope of a descendant:
Once a parser reaches the end-tag of a node, the scope of a node must be
understood to be already closed - i.e. no longer be open for associations of
any kind. That is because no more node will follow that can be said to still
be located inside of the node's scope. Because of that, a parser can only
change its state such that it is consistent with that fact - i.e. the parser's
state must reflect that fact.
