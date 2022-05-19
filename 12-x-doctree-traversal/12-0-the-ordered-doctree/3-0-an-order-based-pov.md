
<!-- ======================================================================= -->
# an order-based point-of-view

Since each tree is isomorphic to a hierarchy of scopes, one can examine the
embedding of a child order in terms of the effects on the tree's hierarchy
of scopes.

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

<!-- ======================================================================= -->
## node 'n' - a generic point of view

Assumed one would first embed the child order of node `n`, one can state
that the edges in that child order transform the subsequent siblings of `fc`
such that they are descendants to `fc`. Because of that, these nodes and all
of their descendants appear as nodes within the scope of `fc`, in addition
to the descendants `fc` already had - i.e. the descendants of `fc` in the
unordered document tree. Because of that, `fc` will temporarily turn into
the only child of `n`.

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

Continuing with the child order of `r`, one can state that this child order
transforms the subsequent siblings of `n` such that they are subsequent to
`n`, which is why these nodes and all of their descendants appear as
descendants in the scope of `n`, but *not also* in the scope of `fc`.
Hence, node `n` now has node `ns` as a second child.

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
of the child order of `r` does not turn any further node into a node that
is subsequent to `n`.

<!-- ======================================================================= -->
## remarks - the tree's root

Since the child order of `r` has not yet been entirely embedded, one can state
that the remaining edges transform the subsequent siblings of `fs` (including
node `n`) such that they are subsequent to `fs`. Because of that, these nodes
and all of their descendants appear as descendants in the scope of `fs`.

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

Note that node `n` and all of its descendants appear in the scope of `ps`,
but *not also* in the scope of any of the former child nodes of `ps`. Because
of that, node `n` (as the former next subsequent sibling) will turn into the
second child of `ps`.

Note that the tree's root `r` is guaranteed to end up with one child only.
That is because it had no subsequent sibling that could turn into its second
child.
