
<!-- ======================================================================= -->
# a state-based point-of-view

The following is intended to show that the iterative process can be guaranteed
to end in a path graph after a finite amount of iterations. That is because
any leaf, except for one, will be turned into a parent while any parent will
eventually be turned into and remain a parent of one (i.e. a parent that has
one child only). That is, the process will eventually form a tree such that
there is one and only one leaf, while all the parent nodes in it have one
child only - i.e. a path graph - i.e. a trace of nodes.

<!-- ======================================================================= -->
## arbitrary, binary*, unary

```
 source            loop           sink
|-----------|     |------->|     |-------|
| arbitrary | --> | binary | --> | unary |
|-DTU-------|     |<-------|     |-Trace-|
```

Recall that the ordered document tree is formed by embedding the document
tree's child order into the unordered document tree (an **arbitrary tree**).
Furthermore, this order embedding is guaranteed to produce a tree such that
each node in it has no more than two child nodes (a **binary tree**) - its
former first child, and its former next sibling.

* arbitrary tree --> binary tree

Since the iterative process forms child orders based on the tree of the
previous step, and since these child orders are subsequently embedded next,
the overall process can be described to transform one ordered document tree
into another, until each node in the resulting tree has no more than one
child (an **unary tree**) - i.e. a path graph.

* arbitrary tree (--> binary tree)* --> unary tree

Based on the above, the overall process can be seen from a state-based point
of view, if each state is used to classify if the source tree of the next
step is arbitrary, binary or unary:

<!-- ======================================================================= -->
## remarks

```
  step-0        step-1   step-2   step-3
| =========== | ====== | ====== | ====== |
| n           | n      | n      | n      |
| |----->|    | c1     | c1     | c1     |
| c1    c2    | |-->|  | d1     | d1     |
| |-->| |-->| | d1 c2  | |-->|  | d2     |
| d1 d2 d3 d4 | d2 d3  | d2 c2  | c2     |
|             |    d4  |    d3  | d3     |
|             |        |    d4  | d4     |
|             |        |        |        |
|-arbitrary---|-binary-|-binary-|-unary--|
```

Note that the overall process can be **guaranteed to end** after a finite
amount of steps since the embedding of a child order will produce a tree
whose root (e.g. `n` in step-1) has no more than one child - i.e. the former
first child (e.g. `c1`) of a parent will not have a next subsequent sibling,
which is why the former first child of a root can be understood to assume a
root-like role.

Note that the embedding of a child order is such that **a parent** in the
source tree is **guaranteed to have a first/left child** in the resulting
tree. In contrary to that, a parent may or may not have a second/right
child. That is, the left/right descriptions have no special order-based
meaning as would be the case in a binary search tree - e.g. the left child
of a parent holds a value that is smaller than the parent's value.

<!-- ======================================================================= -->
## binary*, unary

The following will focus on the effects of embedding a child order into the
node order of a binary tree, which is the result of a pervious embedding.

Note that, if a node `n` has a sibling `s`, then embedding the next child
order may or may not append the node's sibling as a child to that node.
Because of that, there are only a handful of cases to consider for any
node. After all, **any node in a tree is either a leaf ex-or a parent**.

**node (n) is a leaf**

```
case-1    | case-2     | case-3
----------|------------|-----------
(a)   (b) | (c)    (d) | (e)    (f)
=== | === | ==== | === | ==== | ===
 p  |  p  | p    |  p  | p    |  p
 n  |  n  | |->| |  s  | |->| |  n
          | s  n |  n  | n  s |  s
```

(case-1) As can be seen, the order embedding will keep leaf `n` as a leaf, if
that leaf has no sibling `s`. (case-2) The same applies, if that leaf has a
presequent sibling. (case-3) In contrary to that, if the leaf has a subsequent
sibling, then that sibling will become the leaf's one and only child.

- a leaf that has no sibling will remain a leaf
- a first child leaf will become a parent of one
- a second child leaf will remain a leaf

Note that the case of having no subsequent sibling is equivalent to having
no sibling at all - i.e. the one and only child of its parent.

**node (n) is a parent**

```
case-4    | case-5     | case-6
----------|------------|------------
(g)   (h) | (i)    (j) | (k)    (l)
=== | === | ==== | === | ==== | ====
 p  |  p  | p    |  p  | p    | p
 n  |  n  | |->| |  s  | |->| | n
 c  |  c  | s  n |  n  | n  s | |->|
          |    c |  c  | c    | c  s
```

(case-4) As can be seen, the order embedding will keep parent `n` as a parent,
if that parent has no sibling `s`. (case-5) The same applies, if that parent
has a presequent sbiling. (case-6) In contrary to that, if the parent has a
subsequent sibling, then that sibling will become the parent's second child.

- a parent that has no sibling will be a parent of one
- a first child parent will be a parent of two
- a second child parent will be a parent of one

Note that it is secondary to these considerations, if the parent in question
has one or two child nodes. That is because the embedding of the next child
order will focus on the parent's first child, while (if necessary) appending
its next subsequent sibling as a second child.

<!-- ======================================================================= -->
## a state-based point of view

```
   t1            t3            t6
|----->|  t2  |----->|  t4  |----->|
|  L*  | ---> |  P1* | <--> |  P2* |
|<-----|      |<-----|  t5  |<-----|
```

Based on the above, a node may be a leaf (L), a parent of one child (P1) or
a parent of two child nodes (P2). If these options used as states, then only
the following transitions (tX) are possible:

- (t1) A leaf that has no sibling, or a previous sibling, remains to be a leaf.
- (t2) A leaf that has a subsequent sibling will be a parent of one.
- (t3) A parent of one without a sibling, or a parent of one that has a
  presequent sibling, remains to be a parent of one.
- (t4) A parent of one with a subsequent sibling will be a parent of two.
- (t5) A parent of two without a sibling, or a parent of two with a presequent
  sibling will be a parent of one.
- (t6) A parent of two with a subsequent sibling remains to be a parent of two.

Note that a leaf may turn into a parent of one. However, no parent will ever
turn into leaf. In contrary to that, a parent may in principle switch back and
forth between states P1 and P2.

Note that this state machine is not transitive. That is because no leaf will
ever not turn into a parent of two. For that to happen a leaf would need to
have a child. That is, it would need to be a parent, which it isn't.
