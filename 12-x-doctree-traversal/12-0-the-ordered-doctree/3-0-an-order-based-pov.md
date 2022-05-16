
<!-- ======================================================================= -->
# an order-based point-of-view

Since each tree is isomorphic to a hierarchy of scopes, one can examine the
embedding of a child order in terms of its effects on its hierarchy of scopes.

```
         r
         |
 -----------------
 | .. |  |  | .. |
 fs  ps  n  ns  ls
         |
      -------
      | ... |
      fc   lc
```

Assumed one would first embed the child order of node `n`, one can state that
the edges in that child order transform the subsequent siblings of `fc` such
that they are descendants to `fc`. Because of that, these nodes and all of
their descendants appear as nodes within the scope of `fc`, in addition to
the descendants it already had (i.e. its child nodes and their descendants).

```
         r
         |
 ---------------------------
 | .. |   |           | .. |
 fs  ps |-n---------| ns  ls
        | |-fc----| |
        | | .. lc | |
        | |-------| |
        |-----------|
```

Note that, after this intermediate step, node `n` has node `fc` as one and only
only child. After all, each and every descendant is now subsequent to `fc` and
therefore a node in its scope.

Continuing with the child order of `r`, one can state that this child order
transforms the subsequent siblings of `n` such that they are subsequent to
`n`. Because of that, these nodes, including all of their descendants appear
as descendants in the scope of `n`, but *not also* in the scope of `fc`.
Hence, node `n` now has node `ns` as its second child.

```
         r
         |
 ------------------------------
 | .. |   |
 fs  ps |-n-------------------|
        | |-fc----| |-ns----| |
        | | .. lc | | .. ls | |
        | |-------| |-------| |
        |---------------------|
```

Note that, regardless of how many child nodes `n` and `r` had, node `n` is
guaranteed to have no more than two child nodes. That is because the remainder
of the child order of `r` does not define any further node to be subsequent
to node `n`.

Since the child order of `r` has not yet been entirely embedded, one can state
that the remaining edges transform the subsequent siblings of `fs` (including
node `n`) such that they are subsequent to `fs`. Because of that, these nodes
and all of their descendants appear as descendants in the scope of `fs`. Node
`n` and all of its descendants therefore also appear in the scope of `ps`,
but *not also* in the scope of any of the child nodes of `ps`.

```
|-r-------------------------------------|
| |-fs--------------------------------| |
| | .. |-ps-------------------------| | |
| |    | .. |-n-------------------| | | |
| |    |    | |-fc----| |-ns----| | | | |
| |    |    | | .. lc | | .. ls | | | | |
| |    |    | |-------| |-------| | | | |
| |    |    |---------------------| | | |
| |    |----------------------------| | |
| |-----------------------------------| |
|---------------------------------------|
```

Note that the tree's root `r` is guaranteed to end up with one child only.
That is because it had no subsequent sibling that could become a second child.
Based on that, and if one were to embed a second child order, the root's
former first child `fc` would turn into a node with one child only. Based on
that one might assume that **iteratively embedding even more child orders**
will result in a linear order (i.e. a trace of nodes) after a finite amount
of iterations.
