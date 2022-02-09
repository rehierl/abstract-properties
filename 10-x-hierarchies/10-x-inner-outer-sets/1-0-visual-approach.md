
<!-- ======================================================================= -->
# a visual approach

```
the initial node tree      the resulting set of borders
=====================  =>  ============================

     1                      |-----------------------|
 ----------                 | 1     |-------------| |
 2      3                   | |---| | 3           | |
      -----                 | | 2 | | |---| |---| | |
      4   5                 | |---| | | 4 | | 5 | | |
                            |       | |---| |---| | |
                            |       |-------------| |
                            |-----------------------|
```

In order to imagine the set of outer sets `OS(T)`, try the following:

* Draw a node tree onto a piece of paper.
* Surround the whole tree with a border.
* Similar to that, draw a border around each induced subtree.
* Note that any border surrounds a node and all of its descendants.
* Note that there are no borders that cross each other.
* Each border represents a set of nodes, if all edges are removed.
* The set of borders represents the tree's set of outer sets.

Note that a set of outer sets is the family of sets of nodes of each
induced subtree and because of that a hierarchy of scopes.

<!-- ======================================================================= -->
## howto form a hierarchy of scopes

```
tag soup          node tree         set of nodes
============  =>  ============  =>  =============
<1>                    1            |-S0--------|
  2                =========        |     1     |
  <3> 4 </3>       2   3   5        | ========= |
  5                   ===           | 2   3   5 |
</1>                   4            |    ===    |
                                    |     4     |
                                    |-----------|
```

Note that the outer box S0 contains the tree's root node and all of
its descendants. As such it represents the tree's overall set of nodes.

```
                 inner and outer sets
set of nodes     of root node n1
=============    ====================
|-S0--------|    |-S0-oss(n1)------|    |-S0-------------------|
|     1     |    |        1        |    |          1           |
| ========= |    | |-S1-iss(n1)--| |    | |-S2-| |-S3-| |-S4-| |
| 2   3   5 |    | | 2    3    5 | |    | | 2  | | 3  | | 5  | |
|    ===    |    | |     ===     | |    | |----| | == | |----| |
|     4     |    | |      4      | |    |        |  4 |        |
|-----------|    | |-------------| |    |        |----|        |
                 |-----------------|    |----------------------|
```

The entire process is such that one recursively breaks apart the set of nodes
of the source tree. That is, one beings with the root's inner and outer set of
nodes. One then replaces the root's inner set by breaking it apart into the
outer sets of its child nodes. The process then recursively continues with the
outer set of each child node.

```
node tree      set of outer sets              set of outer sets
=========  =>  =========================  =>  =================
    1          |-A---------------------|      A: {1, 2, 3, 4, 5}
=========      | 1                     |      B: {   2         }
2   3   5      | |-B-| |-C-----| |-E-| |      C: {      3, 4   }
   ===         | | 2 | | 3     | | 5 | |      D: {         4   }
    4          | |---| | |-D-| | |---| |      E: {            5}
               |       | | 4 | |       |
               |       | |---| |       |
               |       |-------|       |
               |-----------------------|
```
