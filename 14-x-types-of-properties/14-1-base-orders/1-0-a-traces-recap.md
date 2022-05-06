
<!-- ======================================================================= -->
# pre-order traces, a recap

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
                     |-->| tTR(n)                            over DTR
                     |-tU(n)---------->|                     over DTU
                     |-tO(n)------------------------>|       over DTO
                     |-tPR(n)----------------------------->| over DPR
```

As can be seen, **the scope of a property over any of the these orders**
(i.e. DTR, DTU, DTO and DPR) is a **substring** to the document tree's
pre-order trace. Furthermore, each such scope begins in the defining
node's start-tag and either also ends in that tag, or in the end-tag of
one of the defining node's ancestors.

<!-- ======================================================================= -->
## the pre-order trace over DTR

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
              tTR(n) |-->|
```

The pre-order trace `tTR(n)` of a node in regards to the document tree's
**trivial suborder** (DTR - all of the nodes, none of the edges) is a
1-element substring to the document tree's pre-order trace. After all,
any node has an empty set of descendants in that suborder.

* `TR(N,Ø)` for `T(N,E)`
* `rp(n) := (n)` and `tTR(n) := (n)`

Note that `tTR(n)` begins with the node's start-tag
and **ends with its start-tag**.

<!-- ======================================================================= -->
## the pre-order trace over DTU

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
                     |-tU(n)---------->|
```

* `tU(n) := n × tU(fc) × .. × tU(lc)`
* `( tU(n) substring-of tU(a) )` is true for all `(a in A(n))`

Note that `tU(n)` begins with the node's start-tag
and **ends with its end-tag**.

* `tags(n) := <n> tags(fc) .. tags(lc) </n>`
* `tags(T) := tags(r)` for `(r in RN(T))`

Recall that a pair of tags encloses a node and all of its descendants in DTU.

<!-- ======================================================================= -->
## the pre-order trace over DTO

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
                     |-tO(n)------------------------>|
```

* `tO(n) := tU(n) × tO(ns)`
* `tO(n) := tU(n) × ( tU(ns) × .. × tU(ls) )`
* `( tO(n) substring-of tO(a) )` is true for all `(a in A(n))`

Furthermore ...

* `tU(n) := n × tO(fc)`
* `( tO(c) suffix-of tU(n) )` if `(n parent-of c)`

... which is why ...

* `tO(n) := n × tO(fc) × tO(ns)`

Note that `tO(n)` begins with the node's start-tag
and **ends with the end-tag of the node's parent**.

Note that the pair of tags that consists of the start-tag of a node and the
end-tag of its parent encloses the node and all of its descendants in DTO.
However, only some-of those nodes are its descendants in DTU.

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
                         |-some-of------------------>|
                         |-all-of----->|-none-of---->|
```

Note that, since a node has no more than two child nodes in DTO, and since
**the end-tag of a node** appears just after its last descendant in DTU, that
end-tag can be understood to **separate the descendants of a node** from its
additonal descendants in DTO - i.e. located in between both branches.

<!-- ======================================================================= -->
## the pre-order trace over DPR

```
    <p>               <n>            </n>          </p>  </r>
-----|-----------------|---------------|-------------|-----|
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. × ... |
---------------------|---|-------------|-------------|-----|
|-tPR(T)-------------------------------------------------->|
                     |-tPR(n)----------------------------->|
```

The pre-order trace `tPR(n)` of any node is a **suffix** to the document tree's
pre-order trace `t(T)` (DPR). After all, the ordered sequence of that trace
corresponds with a specialized tree, which is why each node subsequent to a
node is a descendant of that node in that order.

* `tPR(r) := (r,..,n,..,l)`
* `tPR(n) :=      (n,..,l)`

Note that the pre-order trace of any node over the document tree's pre-order
trace is a suffix to the pre-order traces of its ancestors, including that
of the document tree's root.

* `(tPR(n) suffix-of t(T))` for any `(n in N(T))`

Note that `tPR(n)` begins with the node's start-tag
and **ends with the end-tag of the document tree's root**.

Note that the pair of tags that consists of a node's start-tag and the root's
end-tag encloses the node and all of its descendants in DPR.
