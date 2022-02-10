
The **related-to** operator in this sub-chapter
is defined based on the superset-of operator.

- (a < b), (a -> b) := (a **superset-of** b)
- (a < b), (down -> up) := "a" is down, "b" is up

# DI-RE, partial

- allows multiple roots
- allows disconnected items
- **downward-total, not upward-total**
- a set can not have disjoint ancestors
- guaranteed unique rooted paths
- a set may have disjoint descendants
- does not allow parallel subcomponents
- can not support all partial orders

example
- the scopes in a tree/forest
- superset-of is consistent, subset-of is not

# RE-OV, partial

- allows multiple roots
- allows disconnected items
- **not downward-total, not upward-total**
- a set may have overlapping ancestors
- a set may have multiple rooted paths
- a set may have overlapping descendants
- parallel sub-components are possible
- seems to support all partial orders
- e.g. ?!?

# DI-RE-OV, partial

- e.g. ?!?

# RE-only, total

- must have one root and one leaf set only
- e.g. the scopes in a path
