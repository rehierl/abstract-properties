
# variations

many variations are possible, can't cover them all
- e.g. level-, pre-, post-order versions of encodings
- e.g. different kinds of encodings
- e.g. different implementation of each encoding
- focus on the pre-order traversal

purpose of these encodings ..
- Hlen represents HsPre, Hlvl represents HrsPre
- to simplify discussions by reducing the amount
  of variations one needs to keep in mind
- is to allow to easily visualize scopes
- the focus will be on sequences of
  level and length values in pre-order

stack-based implementations
- a stack is consistent with the scope closing order
- last opened, first closed - a consequence of DI-RE
- open/enter a scope => push an item
- close/exit a scope => pop an item
- one usually does not care about the first/root node
- one usually focusses on the last/current node
- one might update the next-to-last/parent node
- in short - rooted paths

# level values, Hlvl

- a hierarchy of level values
- explain - Hlvl <-> Hrp <-> HrsPre
- explain - Hlvl -> Hlen

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- `#s` tells where to place the next element
- `#s` is the element's node level

# length values, Hlen

- a hierarchy of length values
- each value counts the number of nodes in the node's scope
- each value reflects the length of the node's pre-order trace
- explain - Hlen <-> Hpre <-> HsPre
- explain - Hlen -> Hlvl

Hlen - in pre-order
- in regards to streaming large documents
- each node can be treated as a root
- can decode one level at a time
  by skipping over descendants
- can decode in parallel

Hlen - corresponds with a height-map
- seems like that would be helpful for explanations
- could be transformed into a length-based encoding?

# level vs. rank values

node levels as rank values
- a non-tag based notation
- a sequence of rank values

level values vs. rank values
- level values count the number of open scopes
- as instructions to end/close the corresponding scopes
- if generated, they can be relied upon
- not much different to rank values
- level values are absolute

in regards to the level-based encoding
- Note the similarity with rank-based algorithms, which is because the
- current node, assuming all is in order, always is a child to one of
- the nodes in the current rooted path. (More detailed explanations will
- follow eventually).

# meta, next-level

an order-preserving tree traversal must be used
- no operation executed while traversing a tree
  may produce conflicting results

child order
- include the parent as a first node ?
- seems to more closely match the concept of scopes
- seems to cause issues when forming scopes, which
  must not contain the parent/defining node
- still more similar to A*() and D*()
- see the parent-based encoding

if exit-events of multiple scopes match the same end-tag?
- first close the scope with the last defining node?
- issue with different types of sections - section, hx
