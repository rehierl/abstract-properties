
an order-preserving tree traversal must be used
- no operation executed while traversing a tree
  may produce conflicting results

child order
- include the parent as a first node ?
- seems to cause some issues when forming scopes -
  these must not contain the parent/defining node
- might more closely match the concept of scopes
- more similar to A*() and D*()
- see the parent-based encoding

rooted paths
- stack-based implementations
- a stack is consistent with the scope closing order
- last opened, first closed - a consequence of DI-RE
- what if exit-events of multiple scopes match the same end-tag?
- first the scope with the last defining node?
- issue with different types of sections - section, ha

# variations

- many variations are possible, can't cover them all
- e.g. the post-order length- and level-based encodings

purpose of these encodings ..
- Hlen represents HsPre, Hlvl represents HrsPre
- is to simplify discussions by reducing the amount
  of variations one needs to keep in mind
- is to allow to easily visualize scopes
- the focus will be on sequences of
  level and length values in pre-order

# length values, Hlen

- a hierarchy of length values
- each value counts the number of nodes in the node's scope
- each value reflects the length of the node's pre-order trace
- explain - Hlen <-> Hpre <-> HsPre
- explain - Hlen -> Hlvl

pre-order
- in regards to streaming large documents
- each node can be treated as a root
- can decode one level at a time
  by skipping over descendants
- can decode in parallel

# level values, Hlvl

- a hierarchy of level values
- explain - Hlvl <-> Hrp <-> HrsPre
- explain - Hlvl -> Hlen

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- `#s` tells where to place the next element
- `#s` is the element's node level

corresponds with a height-map
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
