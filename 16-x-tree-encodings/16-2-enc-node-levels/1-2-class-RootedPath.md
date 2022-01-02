
<!-- ======================================================================= -->
# the RootedPath helper class

In order to decode a **sequence of level values**, one must maintain a rooted
path which allows to determine the parent of a subsequent node. Overall, this
can be done using a stack-based approach, which can be assumed to be implemented
by the following helper class.

```js
class RootedPath begin
  //- a stack used to keep track of the
  //  nodes in the current rooted path
  stack = ()

  //- the 1-based index of the index of
  //  the node that was set last
  //- initialized to an invalid value
  //- note - nodes at an index whose
  //  value is past 'currentLast' are
  //  considered to be invalid
  currentLast = 0

  //- the functionality of instances of
  //  this class is as can be seen below
end
```

The path's length (aka. max level) can be accessed using the following method.
(Note - not the same as 'stack.size()' or the like).

```js
//- accessible via the "#path" syntax
function length() begin
  return currentLast
end
```

The following method provides random access to any node in the current path.

```js
//- accessible via the "path[index]" syntax
//- level must be a number in [1,currentLast]
function get(index) begin
  assert((0 < index) && (index < currentLast))
  return stack[index]
end
```

A new node can be set using the following method.

```js
//- accessible via the "path[level] = node" syntax
//- level must be a number in [1,size+1]
//- note - the first level given must have value 1
function setLast(level, node) begin
  size = stack.size
  assert((0 < level) && (level <= size+1))

  if (level > size) begin
    stack.append(node)
  else begin
    stack[level] = node
  end

  //- nodes at indexes (i > level) will
  //  be ignored from this point forward
  currentLast = level
end
```
