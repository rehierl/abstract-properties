
- higher level -> a child
- same level -> a sibling to the last
- lower level -> a sibling to an ancestor

rooted paths, stack-based implementations
- a stack is consistent with the scope closing order
- last opened, first closed - a consequence of DI-RE
- open/enter a scope => push an item
- close/exit a scope => pop an item
- one usually does not care about the first/root node
- one usually focusses on the last/current node
- one might update the next-to-last/parent node
- in short - rooted paths

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- `#s` tells where to place the next element
- `#s` is the element's node level

# level vs. rank values

- a first contact with the interaction between
  abstract properties

level values as abstract properties
- decode/read as backwards-oriented instructions
- instructions to end/close the corresponding scopes
- level values count the number of open scopes
- if generated, they can be relied upon
- not much different to rank values
- level values are absolute

node levels as rank values
- a non-tag based notation
- a sequence of rank values

in regards to the level-based encoding
- Note the similarity with rank-based algorithms, which is
- because the current node, assuming all is in order, always
- is a child to one of the nodes in the current rooted path.
- detailed explanations will follow eventually
