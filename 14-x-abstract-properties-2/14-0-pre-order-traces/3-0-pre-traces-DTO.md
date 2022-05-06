
<!-- ======================================================================= -->
# the pre-order trace over DTO

```
    <p>             <n>              </n>          </p>
-----|---------------|-----------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tO(n)------------------------>|
                     |-tU(n)---------->|-suffix----->|
```

Since applying the pre-order rule to node `n` results in prefixing the node's
sequence of subsequent siblings by its sequence of former child nodes, trace
`tU(n)` is a prefix to trace `tO(n)`.

* `tO(n) := ( tU(n) × suffix )`
* `( tU(n) prefix-of tO(n) )` is true

One can then notice that the trace of a node `tU(n)` is followed by the trace
of its next subsequent sibling `tU(ns)`. In other words, the trace of a node
`tO(n)` begins in the node's trace `tU(n)`, which is followed by the traces
of its subsequent siblings, until that sequence ends in the trace of its last
subsequent sibling `tU(ls)`.

* `tO(n) := tU(n) × tU(ns) × .. × tU(ls)`

Based on that, the pre-order trace of a node `tO(n)` can be described as
**a sequence of traces**. Since the **building blocks** of `tO(n)` are traces
over DTU, this seems to suggest that the scope of a node over DTO has some
**level of granularity**. Based on that, the above sub-traces `tU(x)` will
be described as **the atoms** (i.e. indivisible units) of a scope over DTO.

<!-- ======================================================================= -->
## focus on the suffix

```
    <p>             <n>              </n>          </p>
-----|---------------|-----------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tO(n)------------------------>|
                                       |-tO(ns)----->|
```

Note that the trace `tO(n)` begins with start-tag `<n>` and
**ends with the parent's end-tag** `</p>`, not with the node's end-tag.

Note that trace `tO(n)` can also be described such that trace `tU(n)` is
followed by the trace of its next subsequent sibling `tO(ns)`. Because of
that, the trace of a subsequent sibling, can be described as **a suffix**
to the trace of its presequent sibling.

* `tO(n) := tU(n) × tO(ns)`
* `( tO(s) suffix-of tO(n) )`, if `(s subsequent-sibling-of n )`

Note that this can be understood to reflect the scope-based point of view
on ordered sequences - i.e. a hierarchy of scopes/traces.

<!-- ======================================================================= -->
## focus on the prefix

```
    <p>             <n>              </n>          </p>
-----|---------------|-----------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tU(n)---------->|
                     |-n-|-tO(fc)----->|
```

Note that, similar as before and back in regards to DTU, trace `tU(n)` can
be described such that node `n` is follwed by the trace of its first child
`tO(fc)`.

* `tU(n) := n × tO(fc)`
* `tU(n) := n × ( tU(fc) × .. × tU(lc) )`
* `( tO(c) suffix-of tU(n) )` if `( n parent-of c )`

Note that the trace of a node `tO(n)` is a **substring** to the traces of
its ancestors in DTO. However, `tO(n)` is in general neither a prefix nor
a suffix to these traces.

* `( tO(n) substring-of tO(a) )` is true for all `( a in A(n) )`
* `( tO(d) substring-of tU(n) )` is true for all `( d in D(n) )`

<!-- ======================================================================= -->
## a combined point of view

```
    <p>             <n>              </n>          </p>
-----|---------------|-----------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tO(n)------------------------>|
                     |-n-|-tO(fc)----->|-tO(ns)----->|
```

Based on the above, the trace of a node `tO(n)` can be described in terms of
the traces over its child nodes in DTO - i.e. `tO(fc)` and `tO(ns)`.

* `tO(n) := n × tO(fc) × tO(ns)`

Note that this can be understood such that even the ordered document tree has
**an external child order** associated with it - i.e. one that is not (yet)
embedded into the tree order.

* `co(n) := (fc, ns)` over DTO
