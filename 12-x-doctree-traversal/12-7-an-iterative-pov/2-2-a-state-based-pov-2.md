
<!-- ======================================================================= -->
## any parent of two will be a parent of one

```
   t1            t3            t6
|----->|  t2  |----->|  t4  |----->|
|  L*  | ---> |  P1* | <--> |  P2* |
|<-----|      |<-----|  t5  |<-----|
```

As discussed before, a parent of two will remain a parent of two if, and
only if it has a subsequent sibling. Based on the `(P2 -> P2)` loop, one
might fear that the iterative process could loop indefinitely in state P2
for one such parent. Hence, one needs to verify that state P2 is only a
temporary state for any such parent.

```
step-0    step-1    step-2    step-3    step-4    step-5
======= | ======= | ======= | ======= | ======= | ======
 r      |  r      |  r      |  r      |  r      |  r
 |-->|  |  c1     |  c1     |  c1     |  c1     |  c1
 c1 c2  |  |-->|  |  c3     |  c3     |  c3     |  c3
 |-->|  |  c3 c2  |  |-->|  |  n      |  n      |  n
 c3 c4  |  |-->|  |  n  c2  |  |-->|  |  s      |  s
 |-->|  |  n  c4  |  |-->|  |  s  c2  |  |-->|  |  c4
 n   s  |  s      |  s  c4  |  c4     |  c4 c2  |  c2
```

In order to show that the P2 loop is misleading (i.e. only a theoretical
possibility), one might begin with the rooted path of a node (e.g. `rp(n)`)
and attach a subsequent sibling to each node in it. Obviously, the tree's
root can not have such a sibling since it could otherwise not be the root.
Because of that, there will always be at least one node with no such sibling.

Note that the source tree (step-0) has three child orders of two child
nodes - i.e. `(c1,c2)`, `(c3,c4)` and `(n,s)`. Also note that the nodes
in the rooted path `rp(n) := (r,c1,c3,n)` "remain in place". That is,
no node will be pushed in between any of its nodes.

Note that the subsequent siblings will be appended to `rp(n)` "in reversed
order". That is because the sibling of the current last node will be appended
next, while the sibling of an ancestor is first pushed down until it is
turned into the last node's subsequent sibling.

Since the root has no subsequent sibling, the P2-loop will break (at the
latest) with the tree's root. After all, a parent that has no subsequent
sibling will become a parent of one, which is why its former first child
will become a node with no subsequent sibling, and so on. Because of that,
any chain of parent nodes with two child nodes will be resolved in a
downward oriented fashion.

As a matter of consequence, no parent of two will remain a parent of two
indefinitely. That is, any such parent will eventually become a parent
of one after a finite amount of steps.

<!-- ======================================================================= -->
## only one leaf will remain

```
   t1            t3            t6
|----->|  t2  |----->|  t4  |----->|
|  L*  | ---> |  P1* | <--> |  P2* |
|<-----|      |<-----|  t5  |<-----|
```

As discussed before, a leaf will remain a leaf if, and only if it has no
subsequent sibling. Based on the `(L -> L)` loop, one might fear that the
iterative process could loop indefinitely in state L for more than one leaf.

```
step-0   step-1   step-2   step-3
====== | ====== | ====== | ======
 r     |  r     |  r     |  r
 |->|  |  d1    |  d1    |  d1
 d1 n  |  |->|  |  d2    |  d2
 d2 c  |  d2 n  |  |->|  |  d3
 d3    |  d3 c  |  d3 n  |  n
       |        |     c  |  c
```

As can be seen, the iterative process can be described to push down the
branch of a subsequent sibling (e.g. `T[n,*]`), and to narrow down the
width of a tree at a leaf, which is a descendant to the presequent sibling,
until there is only one leaf left.

Note that a binary tree has `(C+1)` leaf nodes, where `C` is the number of
child orders of two nodes. Because of that, and since all of these child
orders will be resolved by this iterative process, one and only one leaf
node will remain. All of the other leaf nodes will be turned into parent
nodes with one child only.

<!-- ======================================================================= -->
## no infinite (P1* <-> P2*) loop

```
r -|-> a5 -|-> a4 -> a3 -|-> a2 -|-> a1 -> n -> c
   |-> s5  |-> s4        |-> s2  |-> s1
```

One can think of a rooted path such that it has disjoint substrings of parent
nodes with two child nodes. Hence, it is possible for nodes to switch back and
forth between states P1 and P2. However, child orders of two nodes will still
be resolved in a downards oriented fashion, which is why any parent of two
will eventually become a parent of one and remain as such until the process
ends.

Note that `a4` is a parent of one (step-0), which will become a parent of two
(child nodes `a3` and `s4`) after the first embedding (step-1). After that, it
will still be a parent of two (child nodes `a3` and `s5`, step-2), before it
will fall back to being a parent of one and remain as such.
