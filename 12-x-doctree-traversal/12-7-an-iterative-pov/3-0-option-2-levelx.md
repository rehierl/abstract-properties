
<!-- ======================================================================= -->
# option-2: (ns -> fc)

```
DTO              reversed
=========   =>   =========
    n                n
    |                |
---------        ---------
|       |        |       |
fc     ns        fc <-- ns
```

Based on the definition of the additional child orders one might already assume
that the resulting trace can not correspond with the pre-order traversal. That
is because this definition will push the next subsequent sibling of each node
in between a node and its former first child. Because of that, the scope of a
node over the unordered document tree will not be a substring to the final
trace - i.e. not in pre-order.

* can not produce the pre-order trace

However, one might assume that this option could be used to produce the
document tree's level-order trace. After all, the first child of each node
will be subsequent to its next sibling and thus not in between both nodes.
That is, the child order of each node might still appear as a substring
to the final trace.

* might produce the level-order trace

<!-- ======================================================================= -->
## example-1: in-order, no-twist

```
doctree                                  trace    node
step-0        step-1   step-2   step-3   step-4   levels
=========== | ====== | ====== | ====== | ====== | ======
p           | p      | p      | p      | p      | 1
|---->|     | n      | n      | n      | n      | 2
n     ns    | |<--|  | ns     | ns     | ns     | 2
|-->| |-->| | c1 ns  | |<--|  | s1     | s1     | 3
c1 c2 s1 s2 | c2 s1  | c1 s1  | |<--|  | s2     | 3
            |    s2  | c2 s2  | c1 s2  | c1     | 3
            |        |        | c2     | c2     | 3
```

As can be seen, this process will produce **a trace of child orders** for
the given input tree. However, the resulting trace is not as required by the
default level-order traversal since `co(ns)` appears presequent to `co(n)`,
which is why this process **can not** result in the default level-order trace.

Note that the resulting trace can still be described as **in level-order**,
it just isn't the default level-order. That is because all of the nodes
still appear **one node-level at a time**.

Note that the additional child orders are **right-to-left oriented** and can
thus to some extend te described as oriented against the child order of the
ordered document tree - e.g. `(ns,c1)` in step-1.

Note that the child order of an intermediate tree is **not first reversed**
before it is embedded. Because of that, **child nodes remain in-place** (aka.
**no twist**). To some extent one can think of the balancing operation in
binary search trees (e.g. AVL trees).

<!-- ======================================================================= -->
## example-2: in-order, do-twist

```
doctree                                                    trace    node
step-0        step-1   step-x   step-2   step-3   step-4   step-5   levels
=========   | ====== | ====== | ====== | ====== | ====== | ====== | ======
p           | p      | p      | p      | p      | p      | p      | 1
|---->|     | n      | n      | n      | n      | n      | n      | 2
n     ns    | |<--|  | |-->|  | ns     | ns     | ns     | ns     | 2
|-->| |-->| | c1 ns  | ns c1  | |<--|  | c1     | c1     | c1     | 3
c1 c2 s1 s2 | c2 s1  | s1 c2  | s1 c1  | |<--|  | s1     | s1     | 3
            |    s2  | s2     | s2 c2  | c2 s1  | |<--|  | c2     | 3
            |        |        |        |    s2  | s2 c2  | s2     | 3
```

As can be seen, first reversing the subsequent child orders before embedding
them into the tree order will result in a sequence of **interleaved** child
orders for the given input tree. However, even though all of the nodes still
appear one node level at a time (i.e. **in level-order**), this process
**can not** result in the default level-order trace. That is because child
orders do not appear as substrings to the final trace.

Note that the child order of an intermediate tree is reversed before it is
embedded. Because of that, **child nodes change sides** (aka. **do twist**).

<!-- ======================================================================= -->
## example-3: reversed, no-twist

```
doctree                                                 trace    node
step-0         step-x        step-1   step-2   step-3   step-4   levels
============ | =========== | ====== | ====== | ====== | ====== | ======
p            | p           | p      | p      | p      | p      | 1
|<----|      | |---->|     | ns     | ns     | ns     | ns     | 2
n     ns     | ns    n     | |<--|  | n      | n      | n      | 2
|<--| |<--|  | |-->| |-->| | s2  n  | |<--|  | c2     | c2     | 3
c1 c2 s1 s2  | s2 s1 c2 c1 | s1 c2  | s2 c2  | |<--|  | c1     | 3
             |             |    c1  | s1 c1  | s2 c1  | s2     | 3
             |             |        |        | s1     | s1     | 3
```

As can be seen, the resulting trace contains the child orders in reversed
order. In addition to that, the **sequence of reversed child orders** is not
as required - i.e. the reversed child order `(s2,s1)` of node `ns` appears
last. Because of that, and even though the resulting trace can be described
as a sequence of reversed child orders, this process can not result in the
default level-order trace. However, the resulting trace still appears to be
**in level-order**.

<!-- ======================================================================= -->
## example-4: reversed, do-twist

```
doctree                                                         trace    node
step-0        step-x        step-1   step-2   step-3   step-4   step-5   levels
=========== | =========== | ====== | ====== | ====== | ====== | ====== | ======
p           | p           | p      | p      | p      | p      | p      | 1
|<----|     | |---->|     | ns     | ns     | ns     | ns     | ns     | 2
n     ns    | ns    n     | |<--|  | n      | n      | n      | n      | 2
|<--| |<--| | |-->| |-->| | s2  n  | |<--|  | s2     | s2     | s2     | 3
c1 c2 s1 s2 | s2 s1 c2 c1 | s1 c2  | c2 s2  | |<--|  | c2     | c2     | 3
            |             |    c1  | c1 s1  | s1 c2  | |<--|  | s1     | 3
            |             |        |        |    c1  | c1 s1  | c1     | 3
```

As can be seen, this process will result in a sequence of **interleaved**
reversed child orders which is **in level-order**.

<!-- ======================================================================= -->
## example-5: in-order, no-twist

```
doctree                                  trace    node
step-0           step-1   step-2   ...   step-6   levels
============== | ====== | ====== | === | ====== | ======
p              | p      | p      |     | p      | 1
|---->|        | n      | n      |     | n      | 2
n     ns       | |<--|  | ns     |     | ns     | 2
|-->| |-->|    | c1 ns  | |<--|  | ... | s1     | 3
c1 c2 s1 s2    | c2 s1  | c1 s1  |     | s2     | 3
         |-->| |    s2  | c2 s2  |     | d1     | 4 (!)
         d1 d2 |    d1  |    d1  |     | d2     | 4
               |    d2  |    d2  |     | c1     | 3
               |        |        |     | c2     | 3
```

As can be seen, this process will push a subsequent sibling and all of its
descendants in between a node and its descendants. Because of that, the
resulting trace is **not in level-order**.

<!-- ======================================================================= -->
## example-6: in-order, do-twist

```
doctree                                              trace    node
step-0           step-1   step-2   step-3   step-4   step-5   levels
============== | ====== | ====== | ====== | ====== | ====== | ======
p              | p      | p      | p      | p      | p      | 1
|---->|        | n      | n      | n      | n      | n      | 2
n     ns       | |<--|  | ns     | ns     | ns     | ns     | 2
|-->| |-->|    | c1 ns  | |<--|  | c1     | c1     | c1     | 3
c1 c2 s1 s2    | c2 s1  | s1 c1  | |<--|  | s1     | s1     | 3
         |-->| |    s2  | s2 c2  | c2 s1  | |<--|  | c2     | 3
         d1 d2 |    d1  | d1     |    s2  | s2 c2  | s2     | 3
               |    d2  | d2     |    d1  | d1     | d1     | 4
               |        |        |    d2  | d2     | d2     | 4
```

As can be seen, the resulting trace is still a sequence of **interleaved**
child orders which is **in level-order**.
