
<!-- ======================================================================= -->
## conclusions

```
       |-oss(n)----------------|
       | |-css(n)-| |-iss(n)-| |
A(n) <---| { .. } | | { .. } |---> D(n)
       | |--------| |--------| |
       |-----------------------|
```

Similar to the inner/outer subset of a set (i.e. `oss(s)`, `iss(s)`),
the CSS of the outer set of a node can be understood to
**bind the outer set of a node to the inner sets of its ancestors**.

<!-- ======================================================================= -->
## conclusion

For each unordered tree of nodes, **only one hierarchy of sets can be formed**
such that the initial node tree can be recreated. That is, only a tree's
hierarchy of outer sets allows to recreate the initial tree. No other hierarchy
of sets of nodes has that characteristic.

That is because ...

* The hierarchy must have one set per node.
  (That is because the relationships of a set defines
  the relationships of the node it represents).
* The CSS of each set must have one and only one element.
  (That is because it must be possible to uniquely
  identify the node of any given set).
* The CE of each set must be the node it represents.
  (That is because it must be possible to determine
  the node a set represents).
* The set of elements `U` is equal the set of nodes `N`.
  (That is a consequence of `(#CSS == 1)` for each set).
* Sets `U`, `P` and `N` have the same number of elements.
  (That is because each element in `U` is a CE).
* The relationships of each set must correspond
  with the relationships of its node.

Note that a node tree has no further information that could be added to a
hierarchy of sets. All the nodes are already part of the hierarchy and the
hierarchy already reflects all relationships of each node.
