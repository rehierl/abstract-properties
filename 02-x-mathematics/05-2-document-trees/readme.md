
# mathematics / document trees

There are some **fundamental differences** between (pure) mathematics and
computer science one should always be aware of:

* Mathematics has no concept of **limited memory**.
  (vs.) Computers always have a finite amount of memory.
* There is only one abstract numeric value 2.
  (vs.) Computers operate on **instances of values**.
  That is, there can be as many 2's as there is memory.
* Containers in Mathematics are by default unordered.
  (vs.) Containers in computers are **always ordered**.
  After all, since memory is always limited, memory must
  be maintained in terms of small chunks, which is why
  non-empty containers always have a first and a last item.

As a consequence of these differences, Mathematics does not seem to support
the concept of a "child order" in the context of node trees. Compared to
that, in Computer Science there is no way around having a child order.

Due to this core difference the child order of a tree is by default treated
as an external extension that is ignored for the most part. As it will turn
out, this "externalization" is the main source of confusion, which is why it
is essential to redefine some terms that are in widespread use. The reasons
as to why the following **re-definitions** are key will be the overall focus.

* (simple) sequence - a sequence whose elements are not required to be unique
* ordered sequence - a sequence that corresponds with a linear/total order
* (simple) tree - a tree whose elements are not required to be unique
* **ordered tree** - corresponds with a partial order - has no child order
* **document tree** (or doctree) - has a child order associated with it
* unordered doctree - the doctree before embedding the child order
* ordered doctree - the doctree after embedding the child order

Note that these **non-standard definitions** will become more clear over time
since subsequent chapters will revisit them in order to clarify certain aspects.

<!-- ======================================================================= -->
## remarks

Note that, as confusing as it might seem at first, no tree, as an abstract
structure of nodes and vertices has a child order. However, a tree may still
have any number of node orders, including a child order, embedded into it.
All of its sub-orders combined can be understood to form the node order of
a tree.

Note that the description "document tree" is intended to be generic and must
as such be understood to refer to both, the ordered and at the same time also
the unordered document tree. Such a description is useful in cases where the
specific node order in question is either unknown or considered non-relevant.

Note that the nodes of a tree can be seen as the components of a complex
value (such as a simple set or a sequence). Based on that point of view,
one should treat node trees the same way as simple sets or sequences -
as **specialized containers**.

Note that the nodes of a document tree can in general be understood to hold
elements (i.e. chunks of content) that can be considered unique. Hence, and
with the notion of an ordered set in mind, any document tree can be described
as an ordered tree.

Note that, unlike sequences, node trees are still somewhat treated as an
extension to Mathematics, even though node trees do correspond with partial
orders. That is, unlike simple sets and sequences, it seems as if node trees
haven't been fully integrated into the very core of Mathematics.
