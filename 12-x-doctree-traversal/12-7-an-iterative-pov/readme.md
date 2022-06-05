
# document traversal / an iterative process

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Since the embedding of a child order will transform the tree's root into a
node that has one child only, one might assume that **iteratively embedding**
even more child orders will result in a linear order after a finite amount
of iterations.

```
DTO              1) in-order        2) reversed
=========   =>   ===========   or   ===========
    n                 n                  n
    |                 |                  |
---------         ---------          ---------
|       |         |       |          |       |
fc     ns         fc --> ns          fc <-- ns
```

Since each node in an ordered document tree has no more than two child
nodes (i.e. **a binary tree**), there are only two options available that
can be used to define subsequent child orders:

**Option-1 (fc -> ns)** - The child order of each node has the former first
child as a first, and the former next sibling as a second/last child -
i.e. **in-order**.

**Option-2 (ns -> fc)** - The child order of each node has the former next
sibling as a first, and the former first child a second/last child -
i.e. **reversed order**.

Note that, since any parent will eventually turn into a parent of one child,
and since any leaf except for one will turn into a parent, the iterative
process is guaranteed to end after **a finite amount of steps**.

Note that neither option is in conflict with the document tree's tree order,
nor with the document tree's child order. After all, the subsequent child
orders do not contradict either order, which is why all of the intermediate
orders and the resulting trace are **order-preserving** in regards to the
document tree.

<!-- ======================================================================= -->
## option 1: (fc -> ns)

```
doctree                         trace
step-0        step-1   step-2   step-3
=========== | ====== | ====== | ======
p           | p      | p      | p
|---->|     | n      | n      | n
n     ns    | |-->|  | c1     | c1   default
|-->| |-->| | c1 ns  | |-->|  | c2   pre-order
c1 c2 s1 s2 | c2 s1  | c2 ns  | ns
            |    s2  |    s1  | s1
            |        |    s2  | s2
```

As can be seen, this option provides an iterative definition for the
**pre-order trace**.

<!-- ======================================================================= -->
## option-2: (ns -> fc)

```
doctree                                              trace    node
step-0           step-1   step-2   step-3   step-4   step-5   levels
============== | ====== | ====== | ====== | ====== | ====== | ======
p              | p      | p      | p      | p      | p      | 1
|---->|        | n      | n      | n      | n      | n      | 2
n     ns       | |<--|  | ns     | ns     | ns     | ns     | 2   some  ?
|-->| |-->|    | c1 ns  | |<--|  | c1     | c1     | c1     | 3   level ?
c1 c2 s1 s2    | c2 s1  | s1 c1  | |<--|  | s1     | s1 (!) | 3   order ?
         |-->| |    s2  | s2 c2  | c2 s1  | |<--|  | c2     | 3
         d1 d2 |    d1  | d1     |    s2  | s2 c2  | s2     | 3
               |    d2  | d2     |    d1  | d1     | d1     | 4
               |        |        |    d2  | d2     | d2     | 4
```

As can be seen, this option can not produce the default level-order trace.
However, it seems as if it may still be used to produce a sequence of
**interleaved child orders** which even seems to be **in level-order** -
i.e. monotone increasing node levels.

Note that, even though this option provides a dual iterative definition for
an order, with no name for it (i.e. not in pre-order, not in post-order, not
the default level-order), this option will not be expanded upon any further.
That is because the focus of this discussion still is on the document order
of a document tree, which is equivalent to the document tree's pre-order
node order.

Note that the order defined by this option may be referred to as
**the iterative level-order**.
