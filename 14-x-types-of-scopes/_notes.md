
apply the pre-order rule to DTO?
- can the pre-order rule be defined
  by repeatedly embedding a child order?
- does a DTO have its own child order?
- `tO(n) := n × tO(fc) × tO(ns)`

about which end-tags can be used
- in order to restrict the scope of a node
- can use the end-tag of any ancestor?
- can use the end-tag of a subsequent sibling?
- issue - there is no sub-order to define it
- issue - no interval

whatwg's "tree order" definition
- similar to that, whatwg's oversimplified perception
  of "ordered set" - treated as equal to "ordered sequence"
- a proper description of "tree order" is a must
- we need to be able to denote the subclass of
  partial orders that correspond with a node tree
- not every partial order is a tree order
- not every tree order is a total order
