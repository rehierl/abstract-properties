
<!-- ======================================================================= -->
# generic rules

```
general node order pattern             |  in short
====================================   |  ===========
p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> s(n)
                      |-> (fc .. lc)   |     |-> c(n)
```

The focus of the following will be on the last siblings of ordered sequences.
That is because each leaf in an ordered doctree is such a node and because no
more than one leaf node may eventually remain. After all, the objective is to
form a total order beginning with the unordered doctree.

Since the last node of a sequence of siblings may still be a parent node, a
**(defining) rule** is required that describes how the sequence of former
child nodes `c(n)` of a node is to be merged with that node and its sequence
of former subsequent siblings `s(n)`. That is, a rule is needed which defines
how to form a new sequence `t` from a node and both of its sequences.

* `t := rule(n,s,c)`

A node will therefore be replaced by the resulting sequence.

* `(.. -> n)` => `(.. -> rule(n,s,c))` => `(.. -> t)`

Note that a defining rule is understood to be **generic** since it must apply
to every single node in the node order.

Note that, due to side effects, applying a rule to one node before another,
may have unintended results. That is, a defining rule may or may not require
a certain **order of execution** to produce an intended result (e.g. pre-order
vs. level-order).

Note that a defining rule must in general not yield a result that is in conflict
with the tree order of an ordered tree (e.g. post-order). That is, a defining
rule must in general be order preserving.

<!-- ======================================================================= -->
## interleaved sequences

Since all of the nodes in sequences `s(n)` and `c(n)` are incomparable, both
sequences may in general be **interleaved**. That is because incomparable
nodes can be, to some extent, ordered arbitrarily without contradicting the
node order of an ordered doctree.

Example: Given two child nodes `c1` and `c2` of a parent `p` in an unordered
doctree, then neither `(p,c1,c2)` nor `(p,c2,c1)` are in conflict with the
orders defined by the edges `(p,c1)` and `(p,c2)`. That is, `p` is in both
sequences presequent to its child nodes. And since there is no requirement
that needs to be satisfied, one can arbitrarily choose one order over the
other.

A rule may in general define to form a sequence by appending all the nodes
from one, before continuing to append the nodes from the other. That is, the
source sequences of two adjacent nodes in the resulting sequence (i.e. the
sequences from which both nodes were taken) may in general alternate. In other
words, two adjacent nodes in the resulting sequence may have distinct source
sequences.

Since there is in general no requirement as to how many siblings a node needs
to have, the sequence of former subsequent siblings, and the sequence of former
child nodes may both have any number of nodes. And since there is no guarantee
in regards to the number of nodes involved, how can one generically define how
both sequences need to be interleaved?

A straight forward answer is: **all-of** (yes, these quantifiers .. again) the
nodes of one sequence (i.e. no exception) are moved before all of the nodes of
the other. That is, one sequence is prefixed by the other. Since each node in
an ordered tree has no more than two child nodes, there are only two options
available:

```
ordered tree            1: pre-order     2: level-order
============     =>     ============     =============
n -|-> s                n -> (c × s)     n -> (s × c)
   |-> c
```

Based on that, a **concatenation** operation can be understood as a special
case of interleaving two sequences.

Note that, if implemented as such, one will have to keep track of which child
represents the former next subsequent sibling, and which its former first
child. Consequently, and since implementations must be able to distinguish
between both child nodes, some sort of **child order** must be maintained in
the ordered doctree. Other than that, there is no requirement that one child
must be a first child since one must only be able to distinguish one child
from the other.

Note that this "order" is maintained by the DOM tree by using special names
for each child (i.e. `.firstChild` and `.nextSibling`).
