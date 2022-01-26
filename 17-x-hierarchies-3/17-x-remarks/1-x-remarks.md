
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
