
<!-- ======================================================================= -->
# overall remarks

Note that this encoding scheme is **an implicit encoding scheme** since it
doesn't directly encode the edges of a tree. Furthermore, no other encoding
is embedded as an "inner encoding" that would first have to be derived.

Recall that the **level of a node** is defined as the vertex-length of its
rooted path - i.e. `#rp(n)`. That is, the length of a node in a tree is the
number of nodes in its extended set of ancestors - i.e. `#A*(n)`. Consequently,
the level of a node counts the number of scopes to which a given node is an
element. In other words, the level of a node is equal to the number of scopes
that are open while a node is being visited.

* `level(n) := #rp(n)`, alternatively `level(n) := #A*(n)`

Note that level values are **independent of the index order** of a tree's
trace of nodes. Because of that, the PRE-POSTR and POST-PRER correspondences
apply directly, without any further modification.
