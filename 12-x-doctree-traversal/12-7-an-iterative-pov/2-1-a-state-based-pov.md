
<!-- ======================================================================= -->
# a state-based point-of-view

Recall that the subsequent child orders will not produce a conflict with the
tree order of the ordered document tree. That is, the resulting trace will be
overall order-preserving - i.e. in regards to the document tree's tree order
and its child order.

The question is therefore, if the resulting trace of the iterative process
will in general be equal to the pre-order trace of the source tree.

<!-- ======================================================================= -->
## arbitrary, binary*, unary

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

Recall that the ordered document tree is formed by embedding the document
tree's child order into the unordered document tree (an **arbitrary tree**).
Furthermore, this order embedding is guaranteed to produce a tree such that
each node in it has no more than two child nodes (a **binary tree**) - its
former first child, and its former next sibling.

* arbitrary tree => binary tree

Since the iterative process forms a child order based on the tree of the
previous step, and since that child order is embedded next, the overall
process can be described to transform one ordered document tree into
another, until each node in the resulting tree has no more than one
child (an **unary tree** - i.e. a path graph).

* arbitrary tree (=> binary tree)* => unary tree

Note that the overall process is **guaranteed to end** after a finite
amount of steps. That is because the embedding of a child order will produce
a tree whose root (e.g. `n`) has no more than one child - i.e. the former
first child (e.g. `c1`) of a parent will not have a next subsequent sibling,
which is why the former first child of a root can be understood to assume
a root-like role.

Note that the embedding of a child order is such that **a parent** in the
source tree is **guaranteed to have a first/left child** in the resulting
tree. In contrary to that, a parent may or may not have a second/right
child. That is, the left/right descriptions have no special order-based
meaning as they have in a binary search tree (i.e. left child of a parent
holds a value that is smaller than the parent's value).

<!-- ======================================================================= -->
## binary*, unary

The following will focus on the effects of embedding a child order into the
node order of a binary tree, which is the result of a pervious embedding.

Recall that any node in a tree is either a leaf ex-or a parent. Also, if a
node `n` has a sibling `s`, then embedding the next child order may or may
not append the node's sibling as a child to that node. Because of that,
there are only a handful of cases to consider for any given node.

**a node is a leaf**

```
case-1    | case-2     | case-3
----------|------------|-----------
(a)   (b) | (c)    (d) | (e)    (f)
=== | === | ==== | === | ==== | ===
 p  |  p  | p    |  p  | p    |  p
 n  |  n  | |->| |  s  | |->| |  n
          | s  n |  n  | n  s |  s
```

(case-1) As can be seen, the order embedding will keep leaf `n` as a leaf,
if that leaf has no sibling `s`. (case-2) The same applies, if the leaf
has a presequent sibling. (case-3) In contrary to that, if the leaf has
a subsequent sibling, then that sibling will become the leaf's one and
only child.

- a leaf that has no sibling will remain a leaf
- a first child leaf will turn into a parent of one
- a second child leaf will remain a leaf

Note that the case of having no subsequent sibling is equivalent to having
no sibling at all - i.e. the one and only child of its parent.

**a node is a parent**

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
if that parent has no sibling `s`. (case-5) The same applies, if the parent
has a presequent sbiling. (case-6) In contrary to that, if the parent has a
subsequent sibling, that sibling will become the parent's second child.

- a parent that has no sibling will be a parent of one
- a first child parent will be a parent of two
- a second child parent will be a parent of one

Note that parent `n` in case-6 may be a parent of two child nodes. In such a
case, that node remains to be a parent of two.

<!-- ======================================================================= -->
## a state-based point of view

```
   t1            t3            t6
|----->|  t2  |----->|  t4  |----->|
|  L*  |----->|  P1* |<====>|  P2* |
|<-----|      |<-----|  t5  |<-----|
```

As can be seen, a node may be a leaf (L), a parent of one child (P1) or a
parent that has two child nodes (P2). With these options as states, the
following transitions are possible:

- (t1) A leaf that has no sibling or a previous sibling remains to be a leaf.
- (t2) A leaf that has a subsequent sibling will turn into a parent of one.
- (t3) A parent of one without a sibling, or a parent of one that has a
  presequent sibling remains to be a parent of one.
- (t4) A parent of one that has a subsequent sibling will turn into a parent
  of two child nodes - i.e. its former child as its first child, and its
  former subsequent sibling as its second child.
- (t5) A parent of two without a sibling, or a parent of two that has a
  presequent sibling will turn into a parent of one one child - i.e. its
  former first child.
- (t6) A parent of two that has a subsequent sibling remains to be a parent
  of two child nodes - i.e. its former first child and its former subsequent
  sibling.

Note that the relation of this the above machine is not transitive. That
is because a leaf can not turn into a parent of two. For that to happen
the leaf would need to have a child. That is it would need to be a parent,
which it isn't.

Note that a leaf may turn into a parent of one. However, no parent will
ever turn into leaf. Compared to that, a parent may in principle switch
back and forth between states P1 and P2.
