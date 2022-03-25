
- TODO - produce traces using each algorithm
- and compare them for equality

<!-- ======================================================================= -->
# in regards to DTU

```
         p          | tree-order:
         |          | top-to-bottom oriented
 -----------------  | "ancestor-of"
 | .. |  |  | .. |  |
 fs  ps  n  ns  ls  | child-order:
         |          | left-to-right oriented
      -------       | "presequent-sibling-of"
      | ... |       |
      fc   lc       |
```

```js
//- the pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  onVisit(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInPreOrder(child);
  }

  //- exit the node's type-1 scope
  //- write("</%s>", name)
  onExitT1(node);
}
```

Note the reversed exit-order. That is, the type-1 scope of a node will be
exited after all type-1 scopes of its descendants have been exited already.

<!-- ======================================================================= -->
# in regards to DTO

```
      presequent          subsequent   |  the resulting tree-order
      siblings            siblings     |  in regards to node (n)
                                       |
p -> (fs .. ps) -> n -|-> (ns .. ls)   |
                      |-> (fc .. lc)   |
                                       |
                          child nodes  |
```

```js
//- the pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  onVisit(node);

  //- recursively visit all child nodes
  if(node.firstChild) {
    traverseInPreOrder(node.firstChild);
  }

  //- exit the node's type-1 scope
  //- write("</%s>", name)
  onExitT1(node);

  //- visit all subsequent siblings
  if(node.nextSibling) {
    traverseInPreOrder(node.nextSibling);
  }

  //- exit the node's type-2 scope
  onExitT2(node);
}
```

<!-- ======================================================================= -->
# html's tree walk

- from the official html specification
- as can be seen - in regards to DTO

```js
function (root, enter, exit) {
  var node = root;

  start: while (node) {
    //- visit the node
    enter(node);

    //- visit all child nodes
    if (node.firstChild) {
      node = node.firstChild;
      continue start;
    }

    while (node) {
      //- exit the node's type-1 scope
      exit(node);

      //- done, if node is the root
      if (node == root) {
        return;
      }

      //- visit all subsequent siblings
      if (node.nextSibling) {
        node = node.nextSibling;
        continue start;
      }

      //- all descendants of the node's
      //  parent have been visited
      node = node.parentNode;
    }//- inner while
  }//- outer while
}//- function
```
