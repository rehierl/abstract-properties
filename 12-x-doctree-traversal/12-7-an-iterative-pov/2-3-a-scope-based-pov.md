
<!-- ======================================================================= -->
# a scope-based pov on option-1

```
         r                       r
         |                       |
 -----------------  =>  ------------------------------  =>  ...
 | .. |  |  | .. |      | .. |   |             |
 fs  ps  n  ns  ls      fs  ps |-n---------| |-ns----|
         |                     | |-fc----| | | .. ls |
      -------                  | | .. lc | | |-------|
      | ... |                  | |-------| |
      fc   lc                  |-----------|
```

Recall that embedding the child order of a document tree into the unordered
document tree has the effect of adding the subsequent siblings (and their
descendants) of the first child `fc` of node `n` to the scope of that first
child. In addition to that, the subsequent siblings of node `n` (and their
descendants) extend the scope of `ns`. Finally, the child order defines node
`ns` to be subsequent to node `n`, which is why the extended scope of `ns`
extends the scope of node `n`, but *not also* the scope of `fc`.

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Due to the above, an ordered document tree is such that each node in it has
no more than two child nodes (i.e. a binary tree) - the node's former first
child `fc` and the node's former next subsequent sibling `ns`.

Note that there is in principle no order over the scopes of `fc` and `ns`,
and therefore also no order over the corresponding nodes. Obviously, option-1
and option-2 both define an order over both nodes.

<!-- ======================================================================= -->
## the first child of a node

```
step-1     step-2
======  |  ======
  n     |    n
|--->|  |    fc
fc  ns  |    ns
```

Since option-1 defines the former first child of a node to be its first child,
all subsequent order embeddings can be understood to preserve the relationship
between a node and its former first child. That is, ..

- **A first child is preserved as the first child of its parent.**

Because of that, a first child is guaranteed to be next subsequent to its
parent in the resulting trace of nodes since option-1 is not defined to push
any other node in between both nodes. After all, the scope of the former next
subsequent sibling will be embedded into the scope of the former first child,
not vice versa.

Recall that the pre-order traversal of a tree visits a node and, right after
that the node's first child. Option-1 can therefore be said to preserve the
**depth-first** characteristic of the pre-order traversal.

- scopes will be entered in pre-order

<!-- ======================================================================= -->

<!-- ======================================================================= -->

TODO
- in between any node and its next subsequent
  sibling will be its descendants

a matter of recursion
- the pre-order traversal of each intermediate tree
