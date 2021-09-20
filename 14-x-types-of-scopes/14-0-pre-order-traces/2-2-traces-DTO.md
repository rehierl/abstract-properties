
<!-- ======================================================================= -->
# the pre-order trace over DTO

```
    <p> ..           <n> ..        </n> ..      </p>
-----|----------------|--------------|------------|---
.. × p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) | ..
---|----------------|----------------|------------|---
                    |-tO(n)---------------------->|
                    |-tU(n)/prefix-->|-suffix---->|
```

Since applying the pre-order rule to node `n` results in prefixing the sequence
of subsequent siblings by the sequence of its child nodes, the pre-order trace
`tU(n)` is consequently a prefix to `tO(n)`.

* `tO(n) := (prefix × suffix)`, where `prefix := tU(n)`
* `(tU(n) prefix-of tO(n))` is true

One can now easily see that the trace of a node `tU(n)` is followed by the trace
of its next subsequent sibling `tU(ns)`, which is then followed by the trace of
its own next subsequent sibling. The trace of a node `tO(n)` is therefore string
of pre-order traces in regards to TU.

In other words, `tO(n)` begins with its own pre-order trace `tU(n)`, followed
by the traces of its subsequent siblings, until that sequence ends in the trace
of its last subsequent sibling `tU(ls)`.

Because of that, the pre-order trace of a node `tO(n)` can be described as
**a string/sequence of pre-order traces**. As such it can be understood to be
formed from **generic units**. Since the **building blocks** of `tO(n)` are
traces over TU, this seems to suggest that the scope of a node over TO has some
level of **granularity**. The above sub-traces could therefore be described as
the atoms (i.e. indivisible units) of a scope over TO.

* `tO(n) := tU(n) × tU(ns) × .. × tU(ls)`

Note that the trace `tO(n)` can also be described such that the trace `tU(n)`
is followed by the trace of its next subsequent sibling `tO(ns)`. This can in
general be understood to reflect the scope-based point of view on ordered
sequences (i.e. a hierarchy of scopes/traces).

* `tO(n) := tU(n) × tO(ns)`
* `(tO(ns) suffix-of tO(n))` is true

Note that, similar as before and back in regards to TU, the trace `tU(n)` can
be described such that node `n` is follwed by the trace of its first child
`tO(fc)`.

* `tU(n) := n × tO(fc)`
* `tU(n) := n × ( tU(fc) × .. × tU(lc) )`
* `(tO(c) suffix-of tU(n))` if `(n parent-of c)`

Note that the trace of a node `tO(n)` is still a substring to all of the traces
of its ancestors in TO. Despite that, `tO(n)` is in general neither a prefix
nor a suffix to the traces of its ancestors.

* `(tO(n) substring-of tO(a))` is true for all `(a in A(n))`
* `(tU(n) superset-of tO(d))` is true for all `(d in D(n))`
