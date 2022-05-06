
<!-- ======================================================================= -->
# more base order candidates?

Note that the relationships between the scopes of base orders is ignored.
That is, the prefix-of relationship between the base orders identified thus
far (i.e. DTR, DTU, DTO, DPR), which is a consequence of the stepwise linear
extension, is not taken into account.

<!-- ======================================================================= -->
## implementation-specific restrictions

Recall that the overall context of this discussion is on the tag-based syntax.
Because of that, **well-defined borders** exist (i.e. the start-tag and the
end-tag of each node) that allow to identify the beginning and the end of a
scope. Furthermore, and due to the overall context, additional borders can
not be introduced.

```
     <n>            </n>          </p>  </a>  </r>
------|---------------|-------------|-----|-----|
... × n × fc .. lc .. × ns .. ls .. × ... × ... |
----|---|-------------|-------------|-----|-----|
    |-tO(n)------------------------>|             over DTO
    |-t???(n)---------------------------->|       over ???
    |-tPR(n)----------------------------------->| over DPR
```

As can be seen, none of the end-tags of any ancestor `a`, other than the
parent `p` of the defining node `n` and the document tree's root `r`, are
used by any of the base orders discussed thus far. The question therefore
is, if the end-tag of such an ancestor could be used as the border of an
additional base order.

Recall that implementations need clear borders since implementations must
always be able to explicitly close each scope. After all, no scope can remain
open once an input document has been processed to the very end. That is, a
consistent design must define explicit endpoints.

<!-- ======================================================================= -->
## the existence of additional ancestors

```
.. <n> .. </n> .. </a> .. </r>
   |-t???(n)-------->|
```

In order for the end-tag of an ancestor to exist, that ancestor must exist.
As a matter of consequence, the corresponding node must have at least one
ancestor in addition to its parent. That requirement is however only met
by the distant (i.e. non-child) descendants of the document tree's root.

```
rp(n) := (r..a..n)
             ?
```

Recall that, except for the root of a tree, each node in a tree has a parent,
which is why the parent's end-tag does in general exist in addition to the
node's own end-tag. However, the root's child nodes are the only nodes such
that the end-tag of their parent (i.e. the root) is equal to the root's
end-tag. That is, the latter two end-tags are all distinct for all of the
other descendants of the root.

Note that, from the perspective of basic definitions, distant (i.e. non-parent)
ancestors can in general not be assumed to exist.

<!-- ======================================================================= -->
## remarks

Assumed that an additional base order had to be included, implementations and
users would have to be made aware of the above mentioned differences between
the nodes. This would obviously **add complexity** to the design, which is
why further base orders will not be taken into account in the context of this
discussion.

* a node (i.e. the current node) exists, and so does its end-tag
* each descendant to the root has a parent, which has an end-tag
* the end-tag of a parent may be equal to the root's end-tag
