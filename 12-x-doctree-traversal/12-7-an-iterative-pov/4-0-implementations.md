
<!-- ======================================================================= -->
# implementations

Given an ordered tree such that a node `n` and its first child `c1` both have
more than one child, then ..

```
step-0     step-x       step-1   step-2   step-3
======== | ========== | ====== | ====== | ======
     n   |   n        | n      | n      | n
   |-->| |   |        | c1     | c1     | c1
   c1 c2 |   c1 -> c2 | |-->|  | d1     | d1
|-->|    |  /   \     | d1 c2  | |-->|  | d2
d1 d2    | d1 -> d2   | d2     | d2 c2  | c2
```

.. embedding the child order `(c1,c2)` of node `n` (step-x) before embedding
the child order `(d1,d2)` of node `c1` will result in an intermediate state
such that the implementation of a node object (e.g. `c1`) must temporarily
support **up to three child nodes**, even though the resulting tree is still
guaranteed to be binary.

```
step-0     step-x   step-1   step-2   step-3
======== | ====== | ====== | ====== | ======
     n   | n      | n      | n      | n
   |-->| | |-->|  | c1     | c1     | c1
   c1 c2 | c1 c2  | |-->|  | d1     | d2
|-->|    | d1     | d1 c2  | |-->|  | d2
d1 d2    | d2     | d2     | d2 c2  | c2
```

In order to avoid such circumstances, child orders should be embedded in
depth-first order - e.g. **in post-order**.
