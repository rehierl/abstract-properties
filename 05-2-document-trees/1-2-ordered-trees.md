
<!-- ======================================================================= -->
# "ordered tree" vs. "simple/unordered tree" (2)

A **(simple) sequence** is such that it has a total index order associated with
the components it holds. Apart from that, a simple sequence is unrestricted in
regards to the elements each of its components may hold. That is, two distinct
components within the same sequence may hold the exact same element. As such,
a (simple) sequence can not be understood to correspond with an ordered set of
elements.

An **ordered sequence** is defined as a sequence such that no two components
in it may hold the exact same element. Because of that, each ordered sequence
can be said to define a total order over the distinct elements it holds. The
description of a sequence as an "ordered sequence" can therefore be understood
to denote the correspondence with an "ordered set" of elements that is
associated with a total order - the index order in case of an ordered sequence.

In regards to that order-based point of view, one can redefine the meaning of
the desciption of a tree as an "ordered tree":

<!-- ======================================================================= -->
## ordered tree

An **ordered tree** is an arborescence such that each node in it can be
considered distinct from all the other nodes. Defined as such, an ordered tree
can be said to define a partial order over the nodes it holds. The description
of a tree as an "ordered tree" can therefore be understood to denote the
correspondence with an "ordered set" of elements that is associated with a
partial order.

Note that, defined as such, an ordered tree does not include the concept of
"child order". However, one can describe a document tree as an ordered tree
that has a child order associated with it.

Note that, defined as such, the nodes of a tree can be understood to implement
the concept of components as introduced with multisets. With that in mind,
**the nodes of a tree are abstract containers of elements**. The difference
in regards to the components of a sequence is therefore that there is no total
(index) order defined over these components, but a partial order. In the context
of an ordered tree, that node order is, similar to the index-order in an ordered
sequence, understood to carry over to the elements each node contains. Based
on that, node trees can be understood to define yet another **type fo container**.
Consequently, and with "sets of elements" and "sequences of elements" in mind,
node trees can and should be perceived as **trees of elements**.

<!-- ======================================================================= -->
## simple/unordered tree

The description of a tree as a **simple tree**, or as an **unordered tree** can
thus be understood to denote that it does not define an ordered set of nodes.
That is, this description can be understood to point out that the nodes in it
are neither required nor expected to be unique.

In that regards, binary search trees could be described as unordered trees since
in principle they allow multiple occurrences of the same entry. Even though such
a search tree has a child order associated with it, describing them as "unordered
trees" does not seem to fit their purpose. Because of that, describing them as
"sorted binary trees" (alt. standard) seems to be more appropriate.

<!-- ======================================================================= -->
## alternatively - linear/total sequence - meh (!)

One might assume that describing an ordered sequence as a "linear/total sequence"
could be an appropriate alternative description to "ordered sequence".

Even though it wouldn't be wrong, it certainly overstresses the aspect that
such a sequence is associated with a total order. That is because the pair of
words "linear" and "sequence" consists of words that are quite similar in that
regards.

In addition to that, the linguisitic proximity to ordered sets would be lost.
Because of that, one would scrap the whole point of describing an "ordered
sequence" as an "ordered sequence".

<!-- ======================================================================= -->
## alternatively - partial tree - meh (!)

One might assume that describing describing a tree as a "partial tree" could
be an appropriate alternative to "ordered tree".

As before, it would overstress the "pointer" to what kind of ordered set is
being defined. That is because the pair of words "partial (order)" and "tree"
consists of words that are quite similar in that regards.

In addition to that, the word "partial" by itself is in general also associated
with something that is "incomplete" in some regards. Although that aspect is
fine in regards to partial orders, it isn't in the context of a node tree. So
that description seems to increase the potential to cause unnecessary confusion.
After all, at some point would undoubtedly ask as to how the node tree might be
"incomplete".
