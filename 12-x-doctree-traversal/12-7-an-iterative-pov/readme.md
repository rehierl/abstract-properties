
# document traversal / an iterative process

<!-- ======================================================================= -->
## option-1: (fc -> ns)

```
step-0        step-1   step-2   step-3
=========== | ====== | ====== | ======
p           | p      | p      | p
|----->|    | n      | n      | n
n     ns    | |-->|  | c1     | c1
|-->| |-->| | c1 ns  | |-->|  | c2
c1 c2 s1 s2 | c2 s1  | c2 ns  | ns
            |    s2  |    s1  | s1
            |        |    s2  | s2
```

Note that, based on this basic example, iteratively applying option-1 to the
ordered document tree **seems to produce the pre-order trace (PRED)** of the
source tree.

<!-- ======================================================================= -->
## option-2: (ns -> fs)

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

The trace produced by option-2, regardless of whether the child orders of
each intermediate tree is reversed or not (twist, no-twist), does not produce
a trace that matches the document tree's default level-order trace - i.e.
**can not produce the default level-order trace** - i.e. not a sequence of
child orders that is overall in child order.

Note that the nodes in the resulting trace seem to still appear one level at
a time - i.e. monotone increasing node levels. However, whether these traces
are indeed in level-order, is not in the focus of this discussion.
