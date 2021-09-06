
<!-- ======================================================================= -->
## an alternative reasoning/explanation

Since each tree is isomorphic to a hierarchy of scopes one can examine the
embedding of a child order in terms of its effects on its scopes.

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

Assumed one would first add the child order of node `n`, one can state that
the edges in that order transform the subsequent siblings of `fc` such that
they are subsequent to `fc`. Because of that, these nodes and all of their
descendants appear within the scope of `fc`.

```
         p
         |
 ---------------------------
 | .. |   |           | .. |
 fs  ps |-n---------| ns  ls
        | |-fc----| |
        | | .. lc | |
        | |-------| |
        |-----------|
```

Continuing with the child order of `p`, one can state that the edges in that
order transform the subsequent siblings of `n` such that they are subsequent
to `n`. Because of that, these nodes and all of their descendants appear
within the scope of `n`, but *not also* within the scope of `fc`.

```
         p
         |
 ------------------------------
 | .. |   |
 fs  ps |-n-------------------|
        | |-fc----| |-ns----| |
        | | .. lc | | .. ls | |
        | |-------| |-------| |
        |---------------------|
```

Based on that one can conclude that, regardless of how many child nodes `n`
and `p` had, node `n` is guaranteed to have no more than two child nodes after
embedding the child order of the initial tree.

Since the child order of `p` has not yet been embedded entirely, one can state
that the remaining edges transform the subsequent siblings of `fs` (including
node `n`) such that they are subsequent to `fs`. Because of that, these nodes
and all of their descendants appear within the scope of `fs`. Consequently,
`n` and all of its descendants are also within the scope of `ps`.

```
p -> |-fs------------------------------|
     | ..                              |
     |  |-ps-------------------------| |
     |  | .. |-n-------------------| | |
     |  |    | |-fc----| |-ns----| | | |
     |  |    | | .. lc | | .. ls | | | |
     |  |    | |-------| |-------| | | |
     |  |    |---------------------| | |
     |  |----------------------------| |
     |---------------------------------|
```

Because of that, the tree's root `p` is guaranteed to eventually have one
and only one child node - i.e. if it was a non-leaf root.

```
|-p-----------------------------------|
| |-fs------------------------------| |
| | ..                              | |
| |  |-ps-------------------------| | |
| |  | .. |-n-------------------| | | |
| |  |    | |-fc----| |-ns----| | | | |
| |  |    | | .. lc | | .. ls | | | | |
| |  |    | |-------| |-------| | | | |
| |  |    |---------------------| | | |
| |  |----------------------------| | |
| |---------------------------------| |
|-------------------------------------|
```
