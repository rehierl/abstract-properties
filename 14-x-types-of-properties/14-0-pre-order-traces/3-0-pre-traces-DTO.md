
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
sequence of subsequent siblings by its sequence of former child nodes, the
pre-order trace `tU(n)` is a prefix to `tO(n)`.

* `tO(n) := ( tU(n) × suffix )`
* `( tU(n) prefix-of tO(n) )` is true

One can then notice that the trace of a node `tU(n)` is followed by the trace
of its next subsequent sibling `tU(ns)`. In other words, the trace of a node
`tO(n)` over the ordered document tree begins with the node's pre-order trace
`tU(n)`, which is followed by the traces of its subsequent siblings, until
that sequence ends in the trace of its last subsequent sibling `tU(ls)`.

* `tO(n) := tU(n) × tU(ns) × .. × tU(ls)`

Because of that, the pre-order trace of a node `tO(n)` can be described as
**a string/sequence of traces**. Since the **building blocks** of `tO(n)` are
traces over DTU, this seems to suggest that the scope of a node over DTO has
some **level of granularity** associated with it, which suggests that the
above sub-traces can be described as **the atoms** (i.e. indivisible units)
of a scope over DTO.

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

Note that the trace of a node `tO(n)` begins with the start-tag of a node
`<n>` and **ends with the parent's end-tag** `</p>`, not with the node's
end-tag.

Note that the trace `tO(n)` can also be described such that the trace `tU(n)`
is followed by the trace of its next subsequent sibling `tO(ns)`. Because of
that, the trace of a subsequent sibling `x`, such as `ns`, can be described
as **a suffix/substring** to the trace of a node.

* `tO(n) := tU(n) × tO(ns)`
* `( tO(s) suffix-of tO(n) )` if `(s subsequent-sibling-of n )`

Note that this can be understood to reflect the scope-based point of view on
ordered sequences - i.e. a hierarchy of scopes/traces.

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

Note that, similar as before and back in regards to TU, the trace `tU(n)`
can be described such that node `n` is follwed by the trace of its first
child `tO(fc)`.

* `tU(n) := n × tO(fc)`
* `tU(n) := n × ( tU(fc) × .. × tU(lc) )`
* `( tO(c) suffix-of tU(n) )` if `( n parent-of c )`

Note that the trace of a node `tO(n)` is still a **substring** to all of the
traces of its ancestors in TO. Despite that, `tO(n)` is in general neither
a prefix nor a suffix to the traces of its ancestors.

* `( tO(n) substring-of tO(a) )` is true for all `( a in A(n) )`
* `( tU(n) superset-of tO(d) )` is true for all `( d in D(n) )`

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
the traces over its child nodes - i.e. `tO(fc)` and `tO(ns)`.

* `tO(n) := n × tO(fc) × tO(ns)`
