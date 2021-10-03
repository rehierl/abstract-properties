
- will have to produce traces using each algorithm
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
traverseInPreOrder(node) begin
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  onVisit(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end

  //- exit the node's type-1 scope
  //- write("</%s>", name)
  onExitT1(node)
end
```

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
traverseInPreOrder(node) begin
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  onVisit(node)

  //- visit all child nodes
  if(node.firstChild) begin
    traverseInPreOrder(node.firstChild)
  end

  //- exit the node's type-1 scope
  //- write("</%s>", name)
  onExitT1(node)

  //- visit all subsequent siblings
  if(node.nextSibling) begin
    traverseInPreOrder(node.nextSibling)
  end
end
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
      //- exit the t1 scope
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
