
The **related-to** operator in this sub-chapter
is defined based on the subset-of operator.

- (a < b), (a -> b) := (a **subset-of** b)
- (a < b), (down -> up) := "a" is down, "b" is up

# DI-RE, partial

- allows multiple roots
- allows disconnected items
- **upward-total, not downward-total**
- a set can have disjoint ancestors
- multiple rooted paths are possible
- a set can not have disjoint descendants
- does not allow parallel subcomponents
- can not support all partial orders
- e.g. ?!?

# RE-OV, partial

- allows multiple roots
- allows disconnected items
- **not downward-total, not upward-total**
- a set may have overlapping ancestors
- a set may have multiple rooted paths
- a set may have overlapping descendants
- parallel sub-components are possible
- seems to support all partial orders

example
- the reversed scopes in a tree
- subset-of is consistent, superset-of is not

# DI-RE-OV, partial

- e.g. the reversed scopes in a forest

# RE-only, total

- must have one root and one leaf set only
- e.g. the reversed scopes in a path
