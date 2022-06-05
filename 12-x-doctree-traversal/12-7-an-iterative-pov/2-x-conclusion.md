
<!-- ======================================================================= -->
## option-1: conclusion

```
doctree                         trace
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
ordered document tree **will produce the pre-order trace (PRED)** of the
source tree.

Note that this option does not have to distinguish between no-twist and do-twist
operations (see option-2). That is because subsequent child orders are oriented
consistently with the document tree's child order - i.e. oriented the same way
in a left-to-right fashion.
