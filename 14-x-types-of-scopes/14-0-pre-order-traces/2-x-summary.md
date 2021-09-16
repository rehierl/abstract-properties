
<!-- ======================================================================= -->
# summary: pre-order traces

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Note that the above acronyms denote the following node orders:

* DTR - the (TR)ivial (D)ocument order
* DTU - the (U)nordered (D)ocument (T)ree
* DTO - the (O)rdered (D)ocument (T)ree
* DPR - the (PR)e-order tree traversal

<!-- ======================================================================= -->
## the pre-order trace over DTR

The pre-order trace `tTR(n)` of any node in regards to the trivial suborder
is a 1-element substring to the pre-order trace. After all, any node has an
empty set of descendants in the trivial suborder.

* `tTR(n), t[N] := (n)` for `N := N(G)` and `G := DTR[n]`

Note that `tTR(n)` begins with the node's start-tag
and also ends with the node's start-tag.

<!-- ======================================================================= -->
## the pre-order trace over DTU

```
    <p> ..           <n> ..        </n> ..      </p>
-----|----------------|--------------|------------|---
.. × p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) | ..
---|----------------|----------------|------------|---
                    |-tU(n)--------->|
```

* `tU(n) := n × tU(fc) × .. × tU(lc)`
* `(tU(n) substring-of tU(a))` is true for all `(a in A(n))`

Note that `tU(n)` begins the the node's start-
and ends with the node's end-tag.

* `tags(n) := <n> tags(fc) .. tags(lc) </n>`
* `tags(T) := tags(r)` for `(r in RN(T))`

<!-- ======================================================================= -->
# the pre-order trace over DTO

```
    <p> ..           <n> ..        </n> ..      </p>
-----|----------------|--------------|------------|---
.. × p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) | ..
---|----------------|----------------|------------|---
                    |-tU(n)/prefix-->|-suffix---->|
                    |-tO(n)---------------------->|
```

* `tO(n) := tU(n) × tO(ns)`
* `tO(n) := tU(n) × ( tU(ns) × .. × tU(ls) )`
* `(tO(n) substring-of tO(a))` is true for all `(a in A(n))`

In addition to the above ...

* `tU(n) := n × tO(fc)`
* `(tO(c) suffix-of tU(n))` if `(n parent-of c)`

Note that `tO(n)` begins with the node's start-tag
and ends with its parent's end-tag.

<!-- ======================================================================= -->
## the pre-order trace over DPR

```
<r> ... <p> ... <n> c(n) </n> s(n) </p> s(p) ... </r>
|-t(T)--------------------------------------------->|
                |-tPR(n)--------------------------->|
```

The pre-order trace `tPR(n)` of any node in regards to the document tree's
pre-order trace `t(T)` is a suffix to that trace. After all, the ordered
sequence of that trace corresponds with a tree, which is why every node
subsequent to a given node is a descendant to that node.

* `tPR(r), t(T) := (r,..,n,..,l)`
* `tPR(n), t[N] := (n,..,l)` for `N := N(G)` and `G := DPR[n]`

Note that the pre-order trace of any node over that node order is a suffix
to the pre-order traces of its ancestors, including that of the tree's root.

* `(tPR(n) suffix-of t(T))` for any `(n in N(T))`

Note that `tPR(n)` begins with the node's start-tag
and ends with the root's end-tag.
