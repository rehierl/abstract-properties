
<!-- ======================================================================= -->
# sequences

```
(simple) sequences (linear order)
------------------------
components:  c1 c2 c3
             |  | /
elements:    v1 v2
```

* `s := ( 1, 2, 2, 'a', false, ... )`

Like a simple set, a sequence (aka. **tuple**) of elements is a specialized
multiset such that a total order is associated with the components it contains.
That is, a (simple) sequence can be described as a group of components which
is paired with an order relation.

Each component in a sequence can be understood to be associated with a numeric
id, which is taken from the set of natural numbers (i.e. `(id in [1,*])`) and
unique in regards to the corresponding sequence (i.e. not "globally" unqiue).

Note that, without any further definition, a sequence may in general hold values
of any kind. Also, distinct components may hold the same value/element.

In addition to that, all the components of a sequence `s` of length `(#s == N)`
are required to have ids within the range `[1,N]`. The components of a sequence
can therefore be understood to be ordered in ascending order according to their
corresponding id values. Each non-empty sequence can therefore be understood to
have a 1st and a last component. As such, the id value of a component can be
described as an **index** (value).

Note that, in the context of this discussion, a sequence needs to be understood
as an indexed list of possibly repeating elements. As such, sequences can be
understood to be similar to character-based strings (i.e. lists of symbols).

<!-- ======================================================================= -->
## lookup, read/get, write/set

Each sequence can be understood to be associated with a lookup operation which,
based on the id/index of a compontent, allows to read/get and write/set the
element of the component that has the given id/index. Hence, `s[x]` or `s(x)`
(note - brackets are an issue in the context of the markdown syntax) must be
understood to dereference the corresponding component, without providing direct
external access to it.

* `var x = s(x)` - read the current value of component `cx`
* `s(x) = 123` - write/set the value of component `cx`

Note that the result of such a get/set operation is undefined if there is no
component with the given index. That is, the corresponding operation must be
understood to throw an error.

<!-- ======================================================================= -->
## add, append

The `add()` operation defined for multisets must be understood to cerate a
new component with the next id/index value that is not yet in use by another
component. Hence, the addition of an element to an existing sequence of length
`#s` will create a new component with id `(#s+1)`. Because of that, adding an
element to a sequence will append that element to the end of the sequence. As
such, the `add()` operation is an `append()` operation.

* `append(s,v) := add(s,v)`

<!-- ======================================================================= -->
## (consistent) iteration

```
traceOf(s) begin
  t = ()
  ni = #s
  for i=1 to ni begin
    v = s(i).value
    t.append(v)
  end
  return t
end

s = ( 1, 2, 2, 3 )
s1 = traceOf(s) //- e.g. ( 1, 2, 2, 3 )
s2 = traceOf(s) //- e.g. ( 1, 2, 2, 3 )
```

In the context of sequences, the random iteration over a multiset is redefined
to be consistent. That is, when iterating over a sequence, the elements in that
sequences will be consistently/always retrieved in order, beginning with the
element from the 1st and ending with the element of the last component.

* `(s1 == s2)` with `s1 := traceof(s)` and `s2 := traceof(s)`

<!-- ======================================================================= -->
## equal, unequal, distinct

```
equalTo(s, t) begin
  if (#s != #t) then
    return false
  end if

  for i=1 to min(#s,#t) begin
    if (s(i) != t(i)) then
      return false
    end
  end

  return true
end if
```

* `(s == t) := equalTo(s, t)`
* `(s != t), (s unequal-to t), (s distinct-to/from t) := not (s == t)`

<!-- ======================================================================= -->
## firstIndexOf, indexOf, idx

```
firstIndexOf(s,v) begin
  for i=1 to #s begin
    if (s(i) == v) then
      return i
    end if
  end
  return -1
end
```

Even though the multiplicity operator continues to apply, the index order
defined upon a sequence allows to extend upon that rudimentary lookup
operation in order to return the index of the first element found.

* `idx(s,v), indexOf(s,v) := firstIndexOf(s,v)`

Based on that, the contains() operation could be redefined as follows:

* `contains(s, v) := (idx(s,v) > 0)`

<!-- ======================================================================= -->
## traceOfIndexes

```
traceOfIndexes(s) begin
  t = ()
  for i=1 to #s begin
    t.append(i)
  end
  return t
end
```

This operation is defined to return a sequence of those indexes that are defined
for the given sequence. This operation is of limited use and therefore only
defined for explanatory purposes.

* `s := (a, b, c)`
* `(traceofIndexes(s) == (1, 2, 3))`

<!-- ======================================================================= -->
## removeAt

```
removeAt(s, ix) begin
  //- find and remove the specified component
  //- re-establish the index order
end
```

Since the removal of an element from a sequence does in general break the
consistency of the index order (i.e. produce a gap in the sequence of indexes),
the removal of a component must be defined to re-establish the consistency that
index order.

* `s := (a, b, c)`, `t := removeAt(s, 2)`
* `(traceOfIndexes(t) = (1, 3))` - inconsistent index order (!)

Re-establishing the index-order however is a simple step that merely requires
to update all the ids/indexes of those components that have an index which is
greater than the index of the removed component.

* `(traceofIndexes(t) = (1, 2))` - ok, no "gap"

```
removeAt(s, ix, ...) begin
  //- find and remove all components that
  //  match any of the specified index values
  //- re-establish the index order
end
```

If more than one component needs to be removed, regardless of the elements they
hold, then the update of the index order must in general be performed after all
components have been removed. Otherwise, subsequent index parameters are no
longer valid.

* `s := (a, b, e, z)`
* `removeAt(s, 2, 4) == (a, e)`

<!-- ======================================================================= -->
## removeOnce

```
removeOnce(s, v) begin
  ix = indexOf(s, v)

  if(ix < 1) then
    return
  end if

  removeAt(s, ix)
end
```

Due to the potential breaking change to the index order, the removeOnce() must
be redefined to re-establish the consistency of the index order.

Recall that remove() and removeAll() are, in the context of multisests, defined
to remove all occurrences of the given element. As such, their definition is
based upon removeOnce(), which is why the corresponding definitions need not
be redefined.
