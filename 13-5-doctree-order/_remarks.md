
# to which property/scope does a node belong?

* the scope of a property contains its defining node
  and all the nodes subsequent to it
* consequently, if a node is visited while a property
  still counts as being open, then each of its descendants
  is also within the property's scope
* within the scope, if the defining node is in
  the node's rooted path - i.e. an ancestor
* can associate while entering and while exiting ...
* however, can only associate with a property
  whose scope did not end before exiting a node
* you can associate while exiting,
  you just shouldn't fuck it up ...
* "while entering" is the better choice by far

TODO - Note that future extensions may possibly close the scope of a node
even before the node's end-tag has been reached. - Makes no sense - It does,
but not in regards to the "scope of a node", but in regards to the extended
scope of a child. - can not be in regards to a distant descendant since such
a scope ends even sooner
