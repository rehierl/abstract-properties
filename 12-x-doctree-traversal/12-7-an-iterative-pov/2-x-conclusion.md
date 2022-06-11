
<!-- ======================================================================= -->
## option-1: conclusion

Recall that the subsequent child orders will not introduce any conflict with
the tree order or the child order of the document tree. That is, the resulting
trace will be order-preserving in regards to both suborders.

The open questions are therefore, if the iterative process can be guaranteed
to end after a finite amount of steps, and if it can be guaranteed to produce
the pre-order trace of the source tree.

- Can the process be guaranteed to end after a finite amount of iterations?
- Can it be guaranteed to produce the source tree's pre-order trace?

<!-- ======================================================================= -->
## is guaranteed to end

```
doctree                         trace
step-0        step-1   step-2   step-3
=========== | ====== | ====== | ======
p           | p      | p      | p
|----->|    | n      | n      | n
n     ns    | |-->|  | c1     | c1   in
|-->| |-->| | c1 ns  | |-->|  | c2   pre-order
c1 c2 s1 s2 | c2 s1  | c2 ns  | ns
            |    s2  |    s1  | s1
            |        |    s2  | s2
```

The overall process is **guaranteed to end** after a finite amount of steps
since the embedding of a child order will produce a tree whose root (e.g.
`n` in step-1) has no more than one child - i.e. the former first child (e.g.
`c1`) of a parent will not have a next subsequent sibling, which is why the
former first child of a root can be understood to assume a root-like role.

Note that, one way to imagine the iterative process would be to think of
**a zipper** that, while being closed, has a linear prefix (a rooted path,
e.g. `(p,n)` in step-1) which ends with the topmost parent that has a
child order of two or more nodes. The iterative process wil then extend
that rooted path by one or more nodes (e.g. `c1` in step-2) with each step,
until the resulting order is linear.

<!-- ======================================================================= -->
## forms the pre-order trace

Note that, based on this basic example, iteratively applying option-1 to the
ordered document tree **will produce the pre-order trace (PRED)** of the
source tree.

<!-- ======================================================================= -->
## remarks

Note that with this option one does not have to distinguish between no-twist
and do-twist operations (see option-2). That is because subsequent child orders
are oriented consistently with the document tree's child order - i.e. oriented
the same way in a left-to-right fashion. Put differently, the consistent
orientation of all child orders does not support such a "twist".
