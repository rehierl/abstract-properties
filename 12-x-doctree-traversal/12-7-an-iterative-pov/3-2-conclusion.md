
<!-- ======================================================================= -->
## option-2: conclusion

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

If the child orders are embedded such that the descendants remain "in place"
(i.e. **no-twist**), the resulting trace is **not in level-order**.

Note that this approach appears similar to balancing operations used in the
context of binary search trees. However, one needs to keep in mind that such
operations are in conflict with the tree order. That is because ancestors
will be pushed downwards and descendants will be pushed upwards.

```
doctree                                              trace    node
step-0           step-1   step-2   step-3   step-4   step-5   levels
============== | ====== | ====== | ====== | ====== | ====== | ======
p              | p      | p      | p      | p      | p      | 1
|---->|        | n      | n      | n      | n      | n      | 2
n     ns       | |<--|  | ns     | ns     | ns     | ns     | 2
|-->| |-->|    | c1 ns  | |<--|  | c1     | c1     | c1     | 3
c1 c2 s1 s2    | c2 s1  | s1 c1  | |<--|  | s1     | s1 (!) | 3
         |-->| |    s2  | s2 c2  | c2 s1  | |<--|  | c2     | 3
         d1 d2 |    d1  | d1     |    s2  | s2 c2  | s2     | 3
               |    d2  | d2     |    d1  | d1     | d1     | 4
               |        |        |    d2  | d2     | d2     | 4
```

If the subsequent child orders are however reversed before they are embedded
(i.e. **do-twist**), the resulting trace can be described as a sequence of
**interleaved child orders** which still seems to be **in level-order**.

Note that, from an order-based perspective, reversing the subsequent child
orders before embedding them seems to be the more natural approach. That
is because, even though the resulting trace is not according to the default
level-order trace, that trace can still be described as in level-order.
