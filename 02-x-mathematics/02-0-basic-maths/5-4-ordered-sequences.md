
<!-- ======================================================================= -->
# set-like/ordered/linear sequences

```
(ordered) sequences (linear order)
------------------------
components:  c1 c2 c3
             |  |  |
elements:    v1 v2 v3
```

A sequence will be referred to as **a set-like sequence**, if no element in
it appears more than once. That is, the multiplicity of each element in such
a sequence is, like in simple sets of elements, exactly one/1.

* `(#s == #E(s))` is required to be true
* i.e. `s` has no repeating elements

Defined as such, each element in a set-like sequence can be understood to be
associated with a unique/distinct index. Based on that, the index order in an
ordered sequence can be understood to carry over onto the elements within the
sequence. Consequently, a set-like sequence can be understood to define an
ordered set of elements that is associated with at total/linar order. Set-like
sequences can therefore also be described as **ordered sequences**, or as
**linear sequences** of elements.

* `(s(i) < s(j)) := (i < j)` for `(i,j in [1,#s])`

Note that sequences which contain elements more than once, may be described
as **non-ordered** or as **non-linear sequences**. Based on that, one can
highlight that these sequences do in general not correspond with total orders.

Note that the focus of the subsequent discussion will be on paths of nodes
such that no node within these paths appears more than once. Despite that,
the description as "a set-like/ordered/linear sequence" is intended to point
out that each of these sequences are understood to define total orders of
elements. As such, ordered sequences can be understood to be closely related
to ordered sets of elements. (see - **order theory**).

Note that, similar to describing a set as a "simple set" or as an "ordered
set", a sequence that allows repeated occurrences (i.e. elements may appear
more than once), may be described as **a simple sequence**.

<!-- ======================================================================= -->
## reduce - R(s)

```
reduce(s) begin
   t = ()
   for c in s begin
     if (c.value in E(s)) then
       //- ignore
     else
       t.append(c.value)
     end if
   end
   return t
end
```

Any sequence can be reduced such that only the very first occurrence of each
element is retained. That is, every other occurence of an element is dropped.

* `s := (e1, e2, e3, e2, e1)`
* `R(s) := reduce(s) = (e1, e2, e3)`
* `(#s == #E(s))` is not true
* `(#R(s) == #E(s))` is true

Note that the reduce() operation is understood to return a sub-sequence of the
source sequence. With that in mind, one can detect potential issues by comparing
the length values of the source sequence with the length value of its reduced
sequence - i.e. there is a potential issue if `(#reduce(s) < #s)` is true.
