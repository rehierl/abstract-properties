
<!-- ======================================================================= -->
# option 2: (ns -> fc)

```
DTO              reversed
=========   =>   =========
    n                n
    |                |
---------        ---------
|       |        |       |
fc     ns        fc <-- ns
```

Based on the definition of the additional child orders of **option-2** one
might assume that the iterative process will maintain the tree order of the
document tree and also its child order. After all, the additional child
orders will not be in conflict with any of these orders.

* will be overall order-preserving

However, one might also assume that the resulting trace can not correspond
with the pre-order traversal. That is because this definition will push
the next subsequent sibling of each node in between the node and its former
first child, which is why the scope of each node can not be a substring to
the resulting trace of nodes.

* can not correspond with the pre-order traversal

Because of that, one might assume that this option could be used to produce
the document tree's level-order trace. After all, the first child of each
node will be subsequent to its next sibling.

* might correspond with the level-order traversal

Note that, as can be seen below, this option **does not allow** to produce
**the default level-order trace** of a document tree. However, it does still
seem to allow to produce **some kind of level-order trace**, since the nodes
seem to still appear one node level at a time.

<!-- ======================================================================= -->
## example-1: in-order, no-twist

```
step-0        step-1   step-2   step-3   step-4
=========== | ====== | ====== | ====== | ======
p           | p      | p      | p      | p
|---->|     | n      | n      | n      | n
n     ns    | |<--|  | ns     | ns     | ns
|-->| |-->| | c1 ns  | |<--|  | s1     | s1
c1 c2 s1 s2 | c2 s1  | c1 s1  | |<--|  | s2
            |    s2  | c2 s2  | c1 s2  | c1
            |        |        | c2     | c2
```

As can be seen, this process will produce **a sequence of child orders**
for the given input tree. However, that sequence is not as defined by the
level-order traversal since `co(ns)` appears presequent to `co(n)`, which
is why this process **can not** result in the default level-order trace.

Note that the resulting trace can still be described as **in level-order**,
it just isn't the default level-order. That is because all of the nodes
still appear **one node-level at a time**.

Note that the subsequent child orders are **right-to-left oriented** and
as such oriented against the child order of the ordered document tree -
e.g. `(ns,c1)` in step-1.

Note also, the child order of an intermediate tree is **not first reversed**.
Because of that, child nodes remain in-place (aka. **no twist**).

<!-- ======================================================================= -->
## example-2: in-order, do-twist

```
step-0        step-1   step-x   step-2   step-3   step-4   step-5
=========   | ====== | ====== | ====== | ====== | ====== | ======
p           | p      | p      | p      | p      | p      | p
|---->|     | n      | n      | n      | n      | n      | n
n     ns    | |<--|  | |-->|  | ns     | ns     | ns     | ns
|-->| |-->| | c1 ns  | ns c1  | |<--|  | c1     | c1     | c1
c1 c2 s1 s2 | c2 s1  | s1 c2  | s1 c1  | |<--|  | s1     | s1
            |    s2  | s2     | s2 c2  | c2 s1  | |<--|  | c2
            |        |        |        |    s2  | s2 c2  | s2
```

As can be seen, this process will result in a sequence of **interleaved**
child orders for the given input tree. However, even though all the nodes
appear one node level at a time (i.e. in level-order), this process
**can not** result in the default level-order trace.

Note that the child order of an intermediate tree is first reversed before
it is embedded. Because of that, child nodes **change sides** with their
parents (aka. **with a twist**).

<!-- ======================================================================= -->
## example-3: reversed, no-twist

```
step-0         step-x        step-1   step-2   step-3   step-4
============ | =========== | ====== | ====== | ====== | ======
p            | p           | p      | p      | p      | p
|<----|      | |---->|     | ns     | ns     | ns     | ns
n     ns     | ns    n     | |<--|  | n      | n      | n
|<--| |<--|  | |-->| |-->| | s2  n  | |<--|  | c2     | c2
c1 c2 s1 s2  | s2 s1 c2 c1 | s1 c2  | s2 c2  | |<--|  | c1
             |             |    c1  | s1 c1  | s2 c1  | s2
             |             |        |        | s1     | s1
```

Note that the resulting trace contains the child orders in reversed order.
In addition to that, the sequence of child orders is not as required -
i.e. the child order `(s2,s1)` of `ns` appears last. Because of that,
this process **can not** result in the default level-order trace.

<!-- ======================================================================= -->
## example-4: reversed, do-twist

```
step-0        step-x        step-1   step-2   step-3   step-4   step-5
=========== | =========== | ====== | ====== | ====== | ====== | ======
p           | p           | p      | p      | p      | p      | p
|<----|     | |---->|     | ns     | ns     | ns     | ns     | ns
n     ns    | ns    n     | |<--|  | n      | n      | n      | n
|<--| |<--| | |-->| |-->| | s2  n  | |<--|  | s2     | s2     | s2
c1 c2 s1 s2 | s2 s1 c2 c1 | s1 c2  | c2 s2  | |<--|  | c2     | c2
            |             |    c1  | c1 s1  | s1 c2  | |<--|  | s1
            |             |        |        |    c1  | c1 s1  | c1
```

As can be seen, this process will result in a sequence of **interleaved**
child orders. Because of that, this process **can not** result in the
default level-order trace.
