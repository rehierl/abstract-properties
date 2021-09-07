
* any operation that builds upon the visit order of a node
  must be executed while processing the node's start-tag

Note that, once a parser reaches the end-tag of a node, the scope of a node
must be understood to be closed - i.e. no longer be open for associations of
any kind. That is because no more node will follow that can be said to still
be located inside of the node's scope. (There is a reason as to why an end-tag
is located where it is). Because of that, a parser can only change its state
such that it is consistent with that fact - i.e. the parser's state must
reflect that fact.

Note that, if a node is subsequent to the end-tag of another node, then that
subsequent node can not belong to the end-tag's scope since that scope has
ended just before that end-tag was reached.

# when to associate

* can associate while entering and while exiting ...
* however, can only associate with a property
  whose scope did not end before exiting a node
* you can associate while exiting,
  you just shouldn't fuck it up ...
* "while entering" is the better choice by far

either all in exor none at all

* the scope of a property contains its defining node
  and all the nodes subsequent to it
* if a node is visited while a property is still open,
  then all of its descendants are within the scope
* within the scope, if the defining node is in
  the node's rooted path - i.e. an ancestor

future extensions

* may possibly close the scope of a node?
* type-2 is not "the scope of a node"
* type-2 refers to an extended scope
* the extended scope of a child
* same issues with distant descendants

when to associate - summary

* the pre-order tree traversal is order-preserving
* preserves the tree order and the child order
* the tag-based syntax is based around the scope of a node
* the scope of a node in the unordered doctree
