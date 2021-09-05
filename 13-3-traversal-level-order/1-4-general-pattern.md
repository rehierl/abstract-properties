
<!-- ======================================================================= -->
# the general level-order pattern

The overall pattern of the (default) level-order trace is such that it begins
with a tree's root `r`, immediately followed by the root's child order, and
ending in a leaf `l` which is the last child of some child order.

* `trace(T) := (r, fc, .., lc, .., l)`

<!-- ======================================================================= -->
## node levels

Note that a level-order trace is in general expected to be such that the node
level of subsequent nodes is **monotone increasing**. Because of that, the
traversal must always begin with the tree's root since a root always has
the lowest node level of all the nodes in a tree.

Note that, due to the monotone increasing node levels, a level-order traversal
can be described as being downwards-oriented (i.e. from a root towards its
leaf nodes).

<!-- ======================================================================= -->
## a sequence of child orders

```
trace(T) := (r, fc, .., lc, ............................., l)
                |-co(r)--||-co(fc)-|...|-co(lc)-|...
```

Since child orders will be appended as a whole, the level-order rule guarantees
that the next sibling of a node remains to be its next sibling. That is, child
orders will not be interleaved by other nodes. Because of that, each child order
is **a substring** to the level-order trace. Consequently, a level-order trace
is in essence a sequence of child orders (aka. **building blocks**).

Since the node levels of subsequent nodes in a level-order trace is required
to be monotone increasing, all child orders of a certain node level appear as
**grouped child orders** in a level-order trace. Put differently, the node
levels in a trace remain constant over all the nodes of one level. Once the
first child on the next node level is reached, the node level will increase
by one.
