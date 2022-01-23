
# length values, Hlen

- each value counts the number of nodes in the node's scope
- each value reflects the length of the node's pre-order trace
- allows to easily visualize scopes

streaming large documents
- each node can be treated as a root
- can decode one level at a time
  by skipping over descendants
- can decode concurrently, in parallel

Hlen - corresponds with a height-map
- seems like that would be helpful for explanations
- could be transformed into a length-based encoding?
