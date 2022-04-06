
<!-- ======================================================================= -->
# a clockwise rotation by 90 degrees

```
n -|-> <tag> fc .. lc </tag>
   |-> ns .. ls
```

In order to visualize the overall structure of a tag soup, one can rotate the
tag soup of a document tree, if seen as a horizontal sequence of tags, clockwise
by 90 degrees and then indent all the tags according to the node level of each
node in the unordered document tree.

```
rotated clockwise |
by 90 degrees     | scopes
------------------|-------
<p>               |  + s(p)
  fs ..           |  |
  <n>             |  +-+ s(n)
    fc .. lc      |  | |
  </n>            |  | |
  ns ..           |  |
</p>              |  |
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
