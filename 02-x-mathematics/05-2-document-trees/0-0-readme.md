
# document trees
- how to deal with "child order"

There are some **fundamental differences** between (pure) mathematics and
computer science one should always be aware of:

* Mathematics has no concept of limited memory. (-vs-)
  Computers always have a finite amount of memory.
* There is only one abstract numeric value 2. (-vs-)
  Computers are based on instances, there can be
  as many 2's as there is memory.
* Containers in Mathematics are by default unordered. (-vs-)
  In the context of computers, "ordered" containers are more natural.

As a consequence of these differences, Mathematics does not seem to support
the concept of a "child order" in regards to node trees. Compared to that,
in Computer Science there is almost no way around having some sort of child
order. Furthermore, it seems as if node trees are still somewhat treated as
an addition to Mathematics, even though each node tree does correspond with
a partial order.

Because of that it seems essential to redefine some terms that are in widespread
use. The reasons as to why these **redefinitions** are required will be the
overall focus of this discussion.

* (simple) sequence - a sequence whose elements are not required to be unique
* ordered sequence - a sequence that corresponds with a total order
* (simple) tree - a tree whose elements are not required to be unique
* ordered tree - a tree that corresponds with a partial order - no child order

Note that the nodes of a tree can be seen as the components of a complex value.
Based on that point of view, one can treat node trees the same way as sets or
sequences: As specialized multisets.

* document tree (or doctree) - a tree that has a child order associated with it
* unordered doctree - the node order before embedding the child order
* ordered doctree - the node order after embedding the child order

Note that the nodes of a document tree can in general be understood to hold
elements (i.e. chunks of content) that can be considered unique. Hence, and
with the notion of an ordered set in mind, any document tree is considered
to be an ordered tree.
