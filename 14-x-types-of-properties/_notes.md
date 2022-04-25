
apply the pre-order rule to DTO?
- can the pre-order rule be defined
  by repeatedly embedding a child order?
- does a DTO have its own child order?
- `tO(n) := n × tO(fc) × tO(ns)`
- hint - additional base orders?

definition of tree order
- downward-total, but not necessarily also upward-total
- hint - downward-total does not guarantee "one root only"

whatwg's "tree order" definition
- similar to that, whatwg's oversimplified perception
  of "ordered set" - treated as equal to "ordered sequence"
- a proper description of "tree order" is a must
- we need to be able to denote the subclass of
  partial orders that correspond with a node tree
- not every partial order is a tree order
- not every tree order is a total order
