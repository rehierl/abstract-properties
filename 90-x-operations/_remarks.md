
- to show the use of suborders
- to show the use of types of scopes

removal of a node
- one of the most basic operations is the removal of a node
- seen as the removal of an entire induced subtree
- the removal of a suffix/intervall in regards to its order
- i.e. what effects does the operation on a tree
  have on the tree's underlying partial order?

point out the difference in default cases
- in regards to the removal of an item
- total/sequences - defaults to type-0 scopes
- partial/trees - defaults to type-1 scopes
- we do treat sequences and trees differently

<!-- ======================================================================= -->

remove-2
- ex5 - a suffix from DTO
- ex6 - a node from DTO

extended
- the effects of ex5, ex6 in DTU
- the effects of ex2, ex4 in DTO

remove-3
- ex7 - from DTO, keep s(n)
- ex8 - from DTO, keep c(n)

<!-- ======================================================================= -->
# next-level

relationships between scopes
- relevant if it comes to scopes of multiple properties
- not much of an issue if scopes are related
- an issue if scopes overlap - inconsistent scopes

What does it mean if the to-be-removed node has a characteristic that is
considered to also apply to its descendants (e.g. a specific color)?

After all, once that node was removed, such a characteristic can no longer
apply to its former descendants since the defining node of that characteristic
was removed. The removal of a node may therefore have unintended side effects,
if the operation is restricted to a single node.
