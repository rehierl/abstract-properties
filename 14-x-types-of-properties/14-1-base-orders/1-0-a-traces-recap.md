
<!-- ======================================================================= -->
# summary: pre-order traces

```
DTR --> DTU --> DTO --> DPR
|<- minimal     maximal ->|
```

Note that the above acronyms denote the following **base orders**:

* DTR - the (TR)ivial suborder of the (D)ocument order
* DTU - the (U)nordered (D)ocument (T)ree
* DTO - the (O)rdered (D)ocument (T)ree
* DPR - the (PR)e-order trace of the document tree

Recall that embedding a child order into the unordered document tree (DTU)
will result in the ordered document tree (DTO). After that, applying the
pre-order rule (i.e. embedding the pre-order edges into the document tree)
will result in the document tree's pre-order trace (DPR).

With these steps in mind one can assume the **trivial suborder** (DTR) (i.e.
the document's set of nodes, but with none of the edges) as the starting point
of the above linear extension. That is, one begins with the trivial suborder,
and embeds all of the edges of the unordered doctree into it.

A trivial suborder may therefore be described as **minimal** since it does not
define any structure (aka. maximal disorder/entropy). That is "minimal" must
be understood to be in regards to the amount of edges that have been embedded
into an order. Conversely, a processing order can be described as **maximal**
since the "order" of a total order can not be increased any further.

* a trivial order has minimal "order"
* a total order has maximal "order"

Note that **the scope of a property over any of these base orders** appears
as a substring to the document tree's pre-order trace. Furthermore, each
such scope either ends in the defining node's start tag or in some end-tag
that is subsequent to it.

<!-- ======================================================================= -->
## the pre-order trace over DTR

The pre-order trace `tTR(n)` of a node in regards to the trivial suborder is
a 1-element substring to the pre-order trace. After all, any node has an empty
set of descendants in that trivial suborder.

* `tTR(n), t[N] := (n)` for `N := N(G)` and `G := DTR[n]`

Note that `tTR(n)` begins with the node's start-tag
and **ends with the start-tag of a node**.

<!-- ======================================================================= -->
## the pre-order trace over DTU

```
    <p>               <n>            </n>          </p>
-----|-----------------|---------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tU(n)---------->|
```

* `tU(n) := n × tU(fc) × .. × tU(lc)`
* `( tU(n) substring-of tU(a) )` is true for all `(a in A(n))`

Note that `tU(n)` begins with the node's
start-tag and **ends with the end-tag of a node**.

* `tags(n) := <n> tags(fc) .. tags(lc) </n>`
* `tags(T) := tags(r)` for `(r in RN(T))`

Recall that a pair of tags encloses a node and all of its descendants in DTU.

<!-- ======================================================================= -->
## the pre-order trace over DTO

```
    <p>               <n>            </n>          </p>
-----|-----------------|---------------|-------------|---
.. × p × fs .. ps .. × n × fc .. lc .. × ns .. ls .. | ..
---|-----------------|-----------------|-------------|---
                     |-tO(n)------------------------>|
                     |-tU(n)---------->|-suffix----->|
```

* `tO(n) := tU(n) × tO(ns)`
* `tO(n) := tU(n) × ( tU(ns) × .. × tU(ls) )`
* `( tO(n) substring-of tO(a) )` is true for all `(a in A(n))`

In addition that ...

* `tU(n) := n × tO(fc)`
* `( tO(c) suffix-of tU(n) )` if `(n parent-of c)`

Note that `tO(n)` begins with the node's start-tag
and **ends with the end-tag of the node's parent**.

Note that, since a node has no more than two child nodes in DTO, and since the
end-tag of a node appears just after its last descendant in DTU, the end-tag
of a node can be understood to separate these descendants (i.e. one branch in
DTO) from its other descendants in DTO. That is, the pair of tags that consists
of the start-tag of a node and the end-tag of its parent encloses the node and
all of its descendants in DTO.

<!-- ======================================================================= -->
## the pre-order trace over DPR

```
<r> ... <p> ... <n> c(n) </n> s(n) </p> s(p) ... </r>
 |-t(T)------------------------------------------->|
                 |-tPR(n)------------------------->|
```

The pre-order trace `tPR(n)` of any node in regards to the document tree's
pre-order trace `t(T)` is a suffix to that trace. After all, the ordered
sequence of that trace corresponds with a tree, which is why each node
subsequent to a given node is a descendant to that node.

* `tPR(r), t(T) := (r,..,n,..,l)`
* `tPR(n), t[N] := (n,..,l)` for `N := N(G)` and `G := DPR[n]`

Note that the pre-order trace of any node over that node order is a suffix
to the pre-order traces of its ancestors, including that of the tree's root.

* `(tPR(n) suffix-of t(T))` for any `(n in N(T))`

Note that `tPR(n)` begins with the node's start-tag
and **ends with the end-tag of the document tree's root**.

Note that the pair of tags that consists of a node's start-tag and the root's
end-tag encloses the node and all of its descendants in DPR.
