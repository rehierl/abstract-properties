
# multisets

```
multisets (no order)
---------------------
components:  c1 c3 c2
             |  | /
elements:    v1 v2
```

A complex value that has no further definitions associated with it is in
general referred to as **a (mathematical) group**, or as **a multiset**.
As such, multisets can be described as generic type-less containers.

* `ms := < v1:21, 21, < true, false >, 'd', "abc" >`

<!-- ======================================================================= -->
## add

```
add(ms, v) begin
  //- create a new component c
  //- set v as its value
  //- add c to ms as a component
end
```

Even though abstract values can be considered immutable in regards to formal
considerations, one still needs to provide the means to actually "create"
complex values.

Note that the addition of a value to a multiset will always add the given value
to that multiset, regardless of wether that value is already an element in it
or not.

<!-- ======================================================================= -->
## (random) iteration

```
traceOf(ms) begin
  s = ()
  for c in ms begin
    s.add(c.value)
  end
  return s
end

s = < 1, 2, 2, 3 >
s1 = traceOf(s) //- e.g. ( 2, 1, 3, 2 )
s2 = traceOf(s) //- e.g. ( 3, 2, 1, 2 )
```

Any multiset can be understood to have some means to visit all of its components
which allows to access/read the elements/values they hold. However, one must
keep in mind that, without further definitions, the components will be visited
randomly. That is, subsequent iterations will in general visit the components
in a different order.

* `(si != sj)` is in general true

Based on such iterations, operators can be defined upon multisets. Below are
definitions for operators that are most commonly used within the context of
this discussion. Many more are possible (e.g. isFlat(), isEmpty(), ...)

<!-- ======================================================================= -->
## cardinality

The number of components grouped by a multiset (ms) will be referred to as
its **cardinality**. In the context of multisets and simple sets, the cardinality
may also be referred to as the **size** of that set which is in general denoted
in terms of a **.count** object property. In contrary to that, the cardinality
of a sequence may also be referred to as the **length** of that sequence.

```
cardinalityOf(ms) begin
  n = 0
  for c in ms begin
    n = n + 1
  end
  return n
end
```

* `#ms, #(ms), (cardinality-of ms) := cardinalityOf(ms)`
* `(#ms == 5)` is true

<!-- ======================================================================= -->
## is-empty

For obvious reasons, a multiset is considered empty, if it does cont contain
any component at all. That is, the cardinality of an empty multiset (`Ø`) is
zero. Otherwise, the multiset can be described as being non-empty.

* `(is-empty ms), isEmpty(ms) := (#ms == 0)`

<!-- ======================================================================= -->
## multiplicity

The number of components that contain the abstract value `v1` will be referred
to as the **multiplicity** of that value within the corresponding multiset.

```
multiplicityOf(ms, x) begin
  n = 0
  for c in ms begin
    if (c.value == x) then
      n = n + 1
    end
  end
  return n
end
```

* `#(ms, v1), (multiplicity-of v1 in ms)` :=
  the number of occurences of abstract value `v1` in `ms`
* `(#(ms, v1) == 2)` and `(#(ms, 21) == 2)` are both true

Note that the cardinality of a complex value may or may not be equal to the
number of distinct elements it contains.

<!-- ======================================================================= -->
## contains, element-of

A multiset is said to contain a value/element, if there are one or more
components in it that have the corresponding value as their element.

* `(v in ms), (v element-of ms) := (#(ms,v) > 0)`

Note that multiset `ms` in the expression `(v in ms)` can be seen as a type of
values (aka. domain). That is, `(v in ms)` can also be understood to state that
`v` must be a value within the specified type.

<!-- ======================================================================= -->
## removeOnce

```
removeOnce(ms, v) begin
  for c in ms begin
    if(c.value == v) then
      //- remove compontent c from ms
      return //- the difference
    end
  end
end
```

If the multiplicity of an element is to be reduced by one, then the operation
needs to cancel the removal after the removal of the first occurrence it finds.

Note that the effect of remove() and removeOnce() is identical if the element
specified has an initial multiplicity of 1.

<!-- ======================================================================= -->
## remove, removeAll

```
remove(ms, v) begin
  n = multiplicityOf(ms, v)
  for i=1 to n begin
    removeOnce(ms, v)
  end
end
```

The removal of an element from a multiset will always reduce the multiset's
cardinality by the multiplicity of the element. That is, all occurrences of
the specified value will be removed from the multiset.

* `removeAll(ms, v) := remove(ms, v)`

<!-- ======================================================================= -->
## one-of

In regards to a multiset that consists one component only, it is helpful to
have an easy means to refer to the single element it holds.

```
oneOf(ms) begin
  for c in ms begin
    return c.value
  end
  throw error
end
```

* `oneOf(ms)` := returns a random element in `ms`

Note that this operator will randomly pick an element out of the given multiset,
if it contains more than one component. It can in general not be used to refer
to any particular element contained within a multiset that has more than one
component.

<!-- ======================================================================= -->
## set-of, elements-in, E()

In case of undetermined complex values it helps to have an operator that
allows to form a multiset based on the distinct elements within the complex
value (aka. a simple set of elements).

```
elementsIn(ms) begin
  s = {}
  for c in ms begin
    if(c.value in s) then
      //- ignore c
    else
      s.add(c.value)
    end
  end
  return s
end
```

* `E(ms), setOf(ms) := elementsIn(ms)`
* e.g. `( #E(ms) <= #(ms) )` is always true
* e.g. `( #E(ms) == #(ms) )` may be true
