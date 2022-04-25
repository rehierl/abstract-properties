
<!-- ======================================================================= -->
# more base order candidates?

Note that, at this point, the relationships between the scopes of base orders
is non-relevant. That is, the prefix-of relationship between the base orders
thus far identified (i.e. DTR, DTU, DTO, DPR) needs to be ignored.

<!-- ======================================================================= -->
## implementation-specific restrictions

Recall that the overall context of this discussion is on the tag-based syntax.
Because of that, there are well-defined borders (i.e. the start-tag and the
end-tag of each node) that allow to identify the beginning and the end of each
scope. Furthermore, and due to the overall context, additional borders can not
be introduced.

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
always be able to explicitly close each and every scope. After all, no scope
may remain open once an input document has been processed to the very end.
That is, a consistent design must define explicit endpoints.

<!-- ======================================================================= -->
## the existence of additional ancestors

```
.. <n> .. </n> .. </a> .. </r>
   |-t???(n)-------->|
```

In order for the end-tag of such an ancestor to exist, that ancestor must
exist. That is, the corresponding node must have at least one more ancestor
in addition to its parent. That requirement is however met only by the
descendants of the document tree's root.

```
rp(n) := (r..a..n)
             ?
```

Recall that, except for the root node of a tree, each node in a tree has a
parent, which is why the parent's end-tag does in general exist in addition
to the node's own end-tag. However, the root's child nodes are the only
nodes such that the end-tag of their parent (i.e. the root) is equal to
the root's end-tag since their parent is the tree's root. That is, the
latter two end-tags are all distinct for all of the descendants of the
root's child nodes.

Note that, from the perspective of basic definitions, such ancestors can in
general not be guaranteed to exist.

<!-- ======================================================================= -->
## remarks

Based on the above, and assumed that an additional base order had to be
included, end-users and implementations would have to be aware of of the
differences between the nodes. This additional requirement would obviously
**add complexity** to the design, which is why further base orders will
not be taken into account in the context of this discussion.
