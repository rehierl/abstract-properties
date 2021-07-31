
<!-- ======================================================================= -->
# Index-based intervals

An interval is in general not required to be in regards to real numbers. That
is, intervals can in general be specified in the context of any ordered set of
elements. One does however need to know how to determine which elements are
included and which ones are not.

* `i4 := [c, f]` represents an interval over a known character set

In case of a set of characters/symbols, any symbol `c` is in general associated
with a unique **codepoint** `cp(c)`. That is, each possible symbol is defined
to have its own unique natural number.

Based on that, the characters of a character set (e.g. "ASCII", "UTF-8") can
be understood to be ordered "alphabetically" in ascending order according to
the values of their codepoints. Consequently, a character set can be described
as an ordered sequence of distinct symbols.

Due to the above, and since each character has a unique codepoint, and as such
a unique index associated with it, the above character-based interval `i3`
can be understood to be associated with an index order. Because of that, a
character-based interval can be uderstood to correspond with an index-based
interval.

* `(i4 := [c,f]) <=> (i4 := [99,102])` - in ASCII

One can therefore determine all the other characters that are in between the
endpoints of interval `i3`. That is, all those characters whose codepoints are
withinin the specified range.

Note that isomorphic orders are required. That is the bijection between the set
of characters/symbols and the index order (i.e. the order over all codepoints)
must be known and order-preserving.

* `(x < y) <-> (cp(x) < cp(y))`

<!-- ======================================================================= -->
## intervals over simple sequences

Since any sequence is associated with an index order over its components,
index-based intervals can be used in the context of a known sequence of
elements. However, since an interval over an index order is only defined
to correspond with a set of index values, there needs to be a mapping
between the set of index values an index-based interval defines, and the
squence of elements. Otherwise, one would just end up with a set of numeric
values.

* `s := (a, b, c, a, e)`
* `s[x]` is defined for `(x in [1,#s])`
* `i5 := [2, 4] => { 2, 3, 4 }`

Because of that, a squence of index values must be formed first such that
it holds all the index values in the specified interval, in ascending order.
Then, and only then can each index within that ordered sequence of intervals
be replaced by the symbol within the source sequence at the specified index.

* `( i5 := [2,4] ) => ( t := (2,3,4) ) => ( u := (b,c,a) )`

Note that the entire mapping needs to be understood to be defined in terms of
an operation/function over a given sequence and a pair of index values. That
operation must be understood to be defined to return a **subsequence** within
the given range of index values:

* `op(s,2,4) -> (b,c,a)`
* `s[2,4] := s(2,4) := op(s,2,4)`

Note that, defined as above, both of the endpoints of the specified interval
are included. It is therefore not possible to exclude any of the endpoints.
This definition is however sufficient in the context of this discussion.

<!-- ======================================================================= -->
## interval-based definitions

With index-based intervals over the index-order of a sequence, and with the
mapping between an index-based interval and the elements of a sequence,
alternative interval-based definitions can be provided for the definitions
of "substring", "infix", "prefix" and "suffix":

A sequence `t` is a **substring** to another sequence `s`, if index-based
endpoints `a` and `b` exist where `(a,b in [1,#s])` such that `t` can be
described as an interval of index values over the source sequence `s`.

* `(t substring-of s) := (t == s[a,b])`
* `(t infix-of s) := (t substring-of s)`

Similar to that, index-based definitions can be provided for
**prefix** and **suffix**:

* `(t prefix-of s) := (t == s[*,b])`
* `(t suffix-of s) := (t == s[a,*])`

Note that each of these definitions is said to define **an induced substring**.
That is, given an interval and **a fixed set of rules**, the resulting substrings
can be described as being induced by the input interval and the following set
of rules:

* from the input interval derive the set of index values
* based on these index values form an ordered sequence of indexes
* within this sequence replace each index by the element of the
  source sequence at the specified index/position.

<!-- ======================================================================= -->
## remarks

Note that an index-based interval over a simple sequence may not necessarily
result in an ordered subsequence. That is, the resulting subsequences may still
contain elements more than once. In contrary to that, an index-based interval
over an ordered sequence will always result in an ordered subsequence.

Note that a programming language does in general allow to specify substrings
via an offset and a length value. Such a specification does however still
translate to an index-based interval.

* `s[offset,length] => s[offset,(offset+length-1)]`

Note that the **interval-based perspective** on substrings over sequences of
elements, as introduced above, does correspond with the first-to-last based
perspective in the context of sections. That is, the resulting induced
substring of an interval-based specification has a first and a last element,
and contains every other element in between.

Note that the **(induced) suffix** of a sequence may be denoted using `s[a]`.
Because of that, the current context must always be taken into account in order
to determine if `s[a]` needs to be understood to denote a sequence, or if the
specification is instead intended to denote the element at the specified index.

* `s[a] := s[a,*]`

By default one can assume that `s[e]` is intended to denote the induced suffix
that has element `e` as its first element. After all, the overall focus of this
discussion is on orders, not on isolated elements.

Note that **induced subtrees** will be denoted the same way. That is, `t[n]`
is used to denote the induced subtree `t[n]` in tree `t` that has node `n`
as its root node.
