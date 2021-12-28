
<!-- ======================================================================= -->
# the RootedPath helper class

In order to decode a sequence of length values, one must count down the current
values in order to keep track of the nodes in the current rooted path. Overall,
this can be done using a stack-based approach, which can be assumed to be
implemented by the following `RootedPath` helper class.

```js
class RootedPath begin
  //- a stack used to maintain the
  //  entries in the current path
  stack = ()

  //- the functionality of this class
  //  instances is as can be seen below
end//- class
```

The path's last node (i.e. the current node) can be retrieved using ...

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

The most fundamental method is the `push()` function, which is used to register
the next node with its initial node count.

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

The most important method is the `pop()` function, which must reduce the node
count of the current node by one, and also the node counts of its ancestors.

```js
function pop() begin
  //- first reduce the node counts
  for (i=stack.size to 1) begin
    entry = stack[i]
    //- reduce the node count by 1/one
    entry.remaining -= 1
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

Note that the `pop()` function can be optimized, if one realizes that not all
node counts have to be reduced with each call. That is, the node count of a
parent only has to be updated if the node count of its child did reach zero.
As a matter of clarity, the above pseudocode is kept as is.
