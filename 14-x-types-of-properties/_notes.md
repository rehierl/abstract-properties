
apply the pre-order rule to DTO?
- can the pre-order rule be defined by
  repeatedly embedding a child order?
- does DTO have its own child order?
- `tO(n) := n × tO(fc) × tO(ns)`
- even more base orders?

definition of tree order
- downward-total, but not necessarily also upward-total
- note - downward-total does not enforce "one root only"

whatwg's definition of "tree order"
- whatwg's oversimplified perception of "ordered set"
- i.e. treated as equal to "ordered list/sequence"
- a proper description of "tree order" is a must
- we need to be able to denote the subclass of
  partial orders that correspond with a tree
- not every partial order is a tree order
- not every tree order is a total order
