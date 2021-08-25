
<!-- ======================================================================= -->
## (mathematical) subsequence-of

```
s = ( a, b, c, d, e, f, g, h, i, ... ) - super-sequence/string
t = (          d, e, f,    h         ) - subsequence
u = (          d, e, f, g            ) - subsequence, substring
```

* sequence `t` is a subsequence, but no substring of `s`
* sequence `u` is a subsequence and a substring of `s`
* substring `u` represents an exact pattern in `s`, subsequence `t` does not

In mathematics, sequence `t` is a subsequence of the source sequence `s`, if it
can be formed/derived from `s` by the removal of zero or more components, while
maintaining the relative order between the remaining components. If `t` is a
subsequence to `s`, then `s` may also be described as the **super-sequence**
of `t`.

Note that this is **a removal-based definition**.

Note that the empty sequence `Ø` (**all-of** the elements removed) is a
subsequence to any sequence, including itself. Furthermore, any non-empty
sequence is a subsequence to itself (**none-of** the elements removed).

Note that, if a sequence is formed by removing one or more elements in between
the 1st and last element of the resulting subsequence, then that subsequence is
said to have **a gap**. In addition to that, if `n` elements have been removed
from in between two elements that are adjacent (i.e. next to each other) in the
subsequence, then that subsequence can be said to have **a gap of size n**.

Note that, as a matter of clarity, a substring can be described as
**a subsequence of consecutive elements**. Here, the word "consecutive" is to
be understood in regards to the elements within the supersequence and thus to
point out that the subsequence has no gaps.

<!-- ======================================================================= -->
## (induced) subsequence

Recall that the term "subsequence" is defined based upon the removal of
components (i.e. a removal-based definition). That is, a source sequence is
first cloned. After that, components, including the elements they hold, are
removed from the newly cloned sequence. And, as a last step, the index-order
of the cloned sequence is re-established since the set of index values would
otherwise contain "gaps".

Because of that, a subsequence can be described as being defined by a set of
those elements that need to remain, while maintaining the index order. Based
on that, the index order can be said to be preserved, which is why the creation
of a subsequence can be described as **order preserving**.

One can therefore describe the creation of a subsequence as a process (i.e.
a known ordered set of operations - aka. a **defining rule**) that must be
performed based on a given input. Because of that, the overall process can
be described as being **induced** by the corresponding input (aka.
**defining element**). That is, the input can be understood to define which
operations to execute in what order.

<!-- ======================================================================= -->
## strict/proper-subsequence-of

A subsequence `s` may be described as **a strict subsequence** of sequence `t`,
if `t` has more components than `s`. Put differently, if one or more components
were removed from `t`.

* `(s strict-subsequence-of t) := (s subsequence-of t) and (s != t)`
* `(s strict-subsequence-of t) -> (#s < #t)`

A (strict) subsequence is considered **sub-ordinate** (in regards to its length)
to a super-sequence. Conversely, a super-sequence is considered to be
**super-ordinate** to a (strict) sub-sequence.

<!-- ======================================================================= -->
## (strictly) related

Two sequences are said to be related with each other, if one is a subsequence
of/to the other.

* `(s related-to t) := (s subsequence-of t) or (t subsequence-of s)`
* `(s strictly-related-to t) := (s related-to t) and (s != t)`

Note that it will depend on a given context, if the related-to operator is
based upon the substring-of, or the subsequence-of operator.

As before, this related-to operator can also be understood to be based upon
a clear defintion. After all, **all-of** the elements of one sequences are
still elements in its super-sequence.

<!-- ======================================================================= -->
## overlap

- (warning - no clear definition)
- (it remains to be seen, if such a definition is even required)

Two sequences can be described as overlapping each other, if both can be formed
from a non-empty prefix and suffix, and if the prefix of one is a subsequence
to the other.

* `s := (t × u)` and `x := (y × z)`
* `(x overlaps y) := ((u subsequence-of x) and (t,u,y,z != Ø)) or ..`
* `            .. or ((y subsequence-of s) and (t,u,y,z != Ø))`
