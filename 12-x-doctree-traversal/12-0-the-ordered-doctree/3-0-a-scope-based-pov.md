
<!-- ======================================================================= -->
# a scope-based point-of-view

Since each tree is isomorphic to a hierarchy of scopes, one can examine the
embedding of a child order in terms of the effects on the tree's hierarchy of
scopes.

```
         p
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
the edges in that child order redefine the subsequent siblings of `fc` (and
all of their descendants) such that they are also subsequent to and thus also
descendants to `fc`. Because of that, these nodes (and all of their descendants)
appear as nodes within the scope of `fc`. Hence, `fc` temporarily turns into
the one and only child of `n`.

```
         p                       p
         |                       |
 -----------------  =>  ------------------------------
 | .. |  |  | .. |      | .. |   |             |
 fs  ps  n  ns  ls      fs  ps |-n---------| |-ns----|
         |                     | |-fc----| | | .. ls |
      -------                  | | .. lc | | |-------|
      | ... |                  | |-------| |
      fc   lc                  |-----------|
```

Continuing with the child order of parent `p`, one can state that it redefines
the subsequent siblings of node `n` (and all of their descendants) such that
they also appear within the scope of `ns`. And since that child order also
redefines these nodes (and all of their descendants) to be subsequent to node
`n`, all of these nodes also appear within the scope of `n`, but *not also*
within the scope of `fc`. Because of that, node `n` will have node `fc` as
a first child and node `ns` as a second child.

```
         p                       p
         |                       |
 -----------------  =>  ------------------------------
 | .. |  |  | .. |      | .. |   |
 fs  ps  n  ns  ls      fs  ps |-n-------------------|
         |                     | |-fc----| |-ns----| |
      -------                  | | .. lc | | .. ls | |
      | ... |                  | |-------| |-------| |
      fc   lc                  |---------------------|
```

Note that, regardless of how many child nodes `n` and `p` had, node `n` is
guaranteed to have no more than two child nodes. That is because the remainder
of the tree's child order does not add any other node to the scope of `n`.

Note that the child order of no other ancestor of node `n` (if one exists) will
have such an effect. That is because the scope of node `n` and the scope of a
subsequent sibling of one of its distant ancestors remain disjoint - just as
the scopes of `fc` and `ns` remain disjoint.

<!-- ======================================================================= -->
## remarks - the tree's root

Since the child order of `p` (i.e. the tree's root) has not yet been entirely
embedded, one can state that the remaining edges transform the subsequent
siblings of `fs` (including node `n`) such that they are subsequent to `fs`.
Because of that, these nodes and all of their descendants appear as descendants
within the scope of `fs`.

```
|-p-------------------------------------|
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

Note that node `n` and all of its descendants appear within the scope of its
next presequent sibling `ps`, but *not also* within the scope of any of the
former child nodes of `ps`. Because of that, node `n` (as the former next
subsequent sibling) will turn into the second child of `ps`.

Note that the tree's root `p` is guaranteed to end up with one child only.
That is because it had no subsequent sibling that could have turned into its
second child.
