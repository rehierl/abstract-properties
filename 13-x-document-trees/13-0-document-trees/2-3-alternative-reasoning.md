
<!-- ======================================================================= -->
## an alternative reasoning/explanation

Since each tree is isomorphic to a hierarchy of scopes, one can examine the
embedding of a child order in terms of its effects on its sets of scopes.

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

Assumed one would first add the child order of node `n`, one can state that
the edges in that order transform the subsequent siblings of `fc` such that
they are subsequent to `fc`. Because of that, these nodes and all of their
descendants appear within the scope of `fc`.

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

Continuing with the child order of `r`, one can state that the edges in that
order transform the subsequent siblings of `n` such that they are subsequent
to `n`. Because of that, these nodes, including all of their descendants
appear within the scope of `n`, but *not also* within the scope of `fc`.

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

Based on that one can conclude that, regardless of how many child nodes `n`
and `r` had, node `n` is guaranteed to have no more than two child nodes.

Since the child order of `r` has not yet been embedded in its entirety, one
can state that the remaining edges transform the subsequent siblings of `fs`
(including node `n`) such that they are subsequent to `fs`. Because of that,
these nodes and all of their descendants appear within the scope of `fs`.
Node `n` and all of its descendants therefore also appear within the scope
of `ps`.

```
r -> |-fs--------------------------------|
     | .. |-ps-------------------------| |
     |    | .. |-n-------------------| | |
     |    |    | |-fc----| |-ns----| | | |
     |    |    | | .. lc | | .. ls | | | |
     |    |    | |-------| |-------| | | |
     |    |    |---------------------| | |
     |    |----------------------------| |
     |-----------------------------------|
```

Because of that, the tree's root `r` is guaranteed to have one child node only.

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
