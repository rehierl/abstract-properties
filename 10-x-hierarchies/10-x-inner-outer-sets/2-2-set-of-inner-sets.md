
<!-- ======================================================================= -->
## The set of inner sets

Note that the root of a tree is not an element of any inner set.

Note that the inner sets of leaf nodes are empty `Ø` and that: (a) the empty
set is disjoint to any set - (b) the empty set is a subset to any set - (c)
the empty set is a strict subset to any non-empty set - (d) the empty set is
not a strict subset to itself.

**CLARIFICATION**
The inner set of a leaf node is empty.
(=> no simple setup).

**CLARIFICATION**
The non-empty inner sets of two distinct nodes are either
disjoint ex-or one is a strict subset to the other.
(=> no strict setup).

(1) If node `n1` is an ancestor of `n2`, then the inner set of `n2` is a subset
to the inner set of `n1`. (Note that this is true, even if `n2` is a leaf node:
`n1` has a non-empty inner set and the inner set of `n2` is empty).

(2) If node `n1` is an ancestor of `n2`, then the inner set of `n1` has `n2`
(not `n1`!) as an element, but the inner set of `n2` does not. The inner set
of an ancestor has always more elements than the inner set of a descendant.
That is, the inner set of a descendant is a strict subset to the inner set
of an ancestor. (Note that this is true, even if `n2` is a leaf node).

(3) If two parent nodes are unrelated to one another (i.e. none is an ancestor
of the other), then both non-empty inner sets are disjoint. That is, both sets
have no node in common.

(4) If the inner set of `n1` and/or the inner set of `n2` is empty while
both defining nodes are unrelated with each other (i.e. one or both nodes
are leaf nodes):

(4.1) If `n1` is a parent and `n2` a leaf, then both inner sets are disjoint.
However, the empty inner set of `n2` is also a strict subset to the non-empty
inner set of `n1` even though both nodes are unrelated to each other (i.e.
not ex-or, i.e. disjoint and strictly related)!

(4.2) If `n1` and `n2` are both leaf nodes, then the empty inner sets of both
are disjoint. Also, and even though none of the empty inner sets is a strict
subset to the other, both sets are still simple subsets to each other (i.e.
not ex-or, i.e. disjoint and related)!

Note that the above statement is still true in the context of non-empty inner
sets. In contrary to that, the above statement is in general not true if one
inner set is empty. Because of that, the set of inner sets is none such that
any two inner sets are either disjoint ex-or related. That is because the
inner sets of two nodes may be disjoint and related at the same time.

Note that requirement-2 (i.e. "if coupled, then related") of the definition of
a strict setup merely requires two coupled sets to be related with each other.
That requirement is fulfilled by a set of inner sets since sets can only be
coupled with each other, if the corresponding sets are non-empty.

Note however that a set of inner sets is still no strict setup since it does
not fulfill requirement-1 (i.e. no set may be empty).

**CLARIFICATION**
The set of inner sets is not guaranteed to have a non-empty root set.
(=> no simple hierarchy).

That is because a node tree that has only one root will result in
a set of inner sets that has the empty set as its only element.

**CLARIFICATION**
The CSS of an inner set is not guaranteed to hold a single node.
(=> no strict hierarchy).

(1) The CSS of the inner set of a leaf node is empty.

(2) The CSS of the inner set of a parent node may have one CE per child.
Hence, the CSS of a parent is non-empty and may hold more than one element.
(Note that, in such a case, the parent's CSS is the set of its child nodes).

**CLARIFICATION**
The non-empty inner set of a parent node is unique to that node.
No other node has the exact same non-empty inner set.

(1) If parent node `n1` is an ancestor of `n2`, then the non-empty inner set of
`n1` contains `n2`, but the inner set of `n2` does not. The inner sets of both
nodes are therefore distinct.

(2) If parent node `n1` is unrelated to `n2` (i.e. none is an ancestor of the
other), then the non-empty inner set of `n1` is distinct from the inner set of
`n2` since no descendant of `n1` can also be a descendant of `n2`.

**CLARIFICATION**
The inner set of a node is in general not unique to a node.
In a set of inner sets, `(#P <= #N)` is true.

If a tree has more than one leaf node, then the empty set is the inner set of
more than one node. Because of that, the number of inner sets will in general
be less than the number of nodes in the corresponding tree. In contrary to that,
the number of elements in both sets is equal, if (e.g.) the tree is the rooted
path of another tree (i.e. a path graph).

**CLARIFICATION**
The **set of inner sets** of a tree does is **no (strict) hierarchy**.
