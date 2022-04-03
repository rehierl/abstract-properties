
<!-- ======================================================================= -->
# a clockwise rotation by 90 degrees

```
n -|-> <tag> fc .. lc </tag>
   |-> ns .. ls
```

In order to visualize the general pattern of the node order of a document
tree, one can rotate its tag soup, if seen as a horizontal sequence of tags,
clockwise by 90 degrees and then indent all tags according to the node level
of each node in the unordered document tree.

```
rotated clockwise | in regards    |
by 90 degrees     | to node <n>   | scopes
------------------|---------------|-------
<p>               | presequent-to |  + s(p)
  fs ..           | above-of      |  |
  <n>             |---------------|  +-+ s(n)
    fc .. lc      | subsequent-to |  | |
  </n>            | below-of      |  | |
  ns ..           |               |  |
</p>              |               |  |
```

By looking at the scopes that are drawn to the side, one can state that we
are already familiar with such **a hierarchical listing**: We see it each
time we open a filesystem browser, or when listing our bookmarks in an
internet browser. That is because in both cases the items (i.e. files or
bookmarks) are organized in nested folders.

Note that the core difference to document trees is that such a hierarchical
listing has in general **two types of nodes**: (1) folders which may contain
items and subfolders (by which the hierarchy is established), and (2) items
which may only contain content.

Note also that such a listing has in general a child order which does not
support a concept of position. That is because the child order is in general
such that folders appear first/topmost. Then, within both subgroups, the
entries appear in alphabetical order according to their name. That is, such
a listing has in general a two-staged child order.
