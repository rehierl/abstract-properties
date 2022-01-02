
<!-- ======================================================================= -->
# the RootedPath helper class

In order to decode a **sequence of length values**, one must count down the
current node count which allows to keep track of the nodes in the current
rooted path. Overall, this can be done using a stack-based approach, which
can be assumed to be implemented by the following helper class.

```js
class RootedPath begin
  //- a stack, used to maintain the
  //  entries in the current path
  stack = ()

  //- the functionality of instances of
  //  this class is as can be seen below
end
```

The path's last node can be retrieved using ...

```js
function current() begin
  size = stack.size
  assert(size > 0)
  entry = stack[size]
  return entry.node
end
```

The current node's parent can be retrieved using ...

```js
function parent() begin
  size = stack.size
  assert(size > 1)
  entry = stack[size-1]
  return entry.node
end
```

The most fundamental method is the following function, which is used to
register the next node with its initial node count.

```js
function push(node, count) begin
  entry = new object()
  entry.node = node
  entry.count = count
  entry.remaining = count
  stack.push(entry)

  //- recall the DI-RE case with scopes
  if (stack.size > 1) begin
    size = stack.size
    parent = stack[size-1]
    assert(count <= parent.remaining)
  end
end
```

Note that the node count of a descendant must be smaller or equal to the node
counts of its ancestors. Hence the assertion with the remaining node count of
the stack's current last node.

The most important method is however the following function, which must reduce
the node count of the current node by one, and also the node counts of each of
its ancestors.

```js
function pop() begin
  //- first reduce all node counts
  for (i=stack.size to 1) begin
    stack[i].remaining -= 1
  end

  //- pop entries if necessary
  for (i=stack.size to 1) begin
    //- the current entry is not yet done
    if (stack[i].remaining > 0) break
    //- the current entry is done - drop it
    stack.pop()
  end
end
```

Note that this function can be optimized, if one realizes that not all node
counts have to be reduced with each call. That is, the node count of a parent
only has to be updated if the node count of its child reached a value of zero.
As a matter of clarity, the above pseudocode is kept as is.
