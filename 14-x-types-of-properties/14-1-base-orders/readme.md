
# types of scopes / base orders

```
    (1)     (2)     (3)
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

The above acronyms denote the following orders:

* DTR - the trivial suborder of the document tree
* DTU - the unordered document tree
* DTO - the ordered document tree
* DPR - the pre-order trace of the document tree

The above pictogram denotes the **linear extension** that has the trivial
suborder (DTR) (i.e. the set of nodes, but with none of the edges) as its
starting point. Into that suborder, (1) the edges of the unordered document
tree (DTU) are embedded. After that, the resulting unordered document tree
(DTU) is extended by (2) embedding the edges of the document tree's child
order. After that, the final step is to extend the resulting ordered document
tree (DTO) by (3) embedding those edges that are defined by the pre-order
rule, which will result in the document tree's pre-order trace (DPR).

```
    <p>               <n>            </n>          </p>  </a>  </r>
-----|-----------------|---------------|-------------|-----|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... × ... |
---------------------|---|-------------|-------------|-----|-----|
                     |-->| tTR(n)                                  over DTR
                     |-tU(n)---------->|                           over DTU
                     |-tO(n)------------------------>|             over DTO
                     |-t???(n)---------------------------->|       over ???
                     |-tPR(n)----------------------------------->| over DPR
```

As can be seen, **the scope of a property over any of the these orders**
(i.e. DTR, DTU, DTO and DPR) is a **substring** to the document tree's
pre-order trace. Furthermore, each such scope begins in the defining node's
start-tag and either also ends in that start-tag, or in the end-tag of one
of the defining node's ancestors.

On top of that, the scope of a node over any of these orders is a **prefix**
to the scopes of those orders that can be understood to have a higher degree
of order (or a lower degree of disorder). In other words, the linear extension
can be understood to have the effect of appending additional descendants to
the trace of a previous step.

Based on **the prefix-of relationship between these orders**, and based on
the fact that these orders have **well defined borders** (i.e. begin in the
defining node's start-tag, and end in its start-tag or the end-tag of one
of its ancestors), these node orders will be referred to as **base orders**.
That is because these orders will be used to form scopes, which are defined
as open intervals - i.e. `s(n) := [n,*]`.

Note that **additional base orders** (i.e. `t???(n)`) are, from a theoretical
point of view, not impossible. However, the would **add additional complexity**
to the base design whose foundation is being layed out by this discussion,
which is why they appear to be **ill advised** to be included by default.
