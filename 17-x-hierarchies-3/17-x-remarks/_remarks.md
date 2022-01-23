
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
