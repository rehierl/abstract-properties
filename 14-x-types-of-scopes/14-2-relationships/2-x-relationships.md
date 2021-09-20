
<!-- ======================================================================= -->
# remarks - hierarchical systems of base orders (?)

Note that a base order is in principle not required to appear as a substring to
the processing order (i.e. no other node in between its nodes) - however, since
the trivial suborder, the unordered doctree and the ordered doctree all contain
all the nodes, each of these base orders is a substring (more accurately equal)
to the processing order.

# n:m relationship

Note that, depending on a given context (i.e. a set of allowed base orders),
any node can in general be understood to be associated with several distinct
non-empty scopes.

Note that each node can be understood to be located within more than one scope.
Because of that, **hierarchies of scopes** are formed based on the nodes the
scopes have in common (e.g. subset-of, substring-of).

# scopes, relationship

Since all the scopes over all the base orders must appear as substrings to the
processing order, one might suspect that it is essential for a system of base
orders that the types of scopes over it must be hierarchical in some way.

case-1
- relationships between the scopes of the same base order
- easy with t1/2 - partial hierarchies of scopes
- easy with t3 - total hierarchies of scopes

case-2, 1-vs-2
- relationships between base orders
- each t1 is disjoint exor related to a t2
- each t2 consists of units of t1

case-3, 1/2-vs-3
- relationships between base orders
- a t3 may overlap a t1/2
  by reaching out of such a scope
- a t3 may contain a t1/2
- a t3 may be disjoint to a t1/2

Note that no t3 scope ends with some internal node (i.e. some, but not all)
of a t1/2 scope. That is because each t1/2 scope is still a suborder to the
t3 base order.

- depending on an application, the t3 base order must be excluded
- without the processing order as a base order, all-exor-none is a consequence
