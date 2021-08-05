
<!-- ======================================================================= -->
# Index-based intervals

An interval is in general not required to be in regards to (real) numbers. That
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
as an ordered sequence of (distinct) symbols.

Due to the above, and since each symbol has a unique index associated with it
(i.e. its codepoint), the character-based interval `i4` can be understood to
be associated with an index order. Because of that, the character-based interval
can be uderstood to correspond with the index-based interval `i5`.

* `(i4 := [c,f]) <=> (i5 := [99,102])` - in ASCII

One can therefore determine all the other characters that are in between the
endpoints of the ascii-based interval `i4`. That is, all of those characters
are included whose codepoints are withinin the range that is specified by `i5`.

Note that isomorphic orders are required. That is the bijection between the set
of characters/symbols and the index order (i.e. the order over all codepoints)
must be known and order-preserving.

* `(x < y) <-> (cp(x) < cp(y))`

<!-- ======================================================================= -->
## intervals over simple sequences

Since any sequence is associated with an index order over its components,
index-based intervals can be used in the context of any known sequence. However,
since an interval over an index order (strictly speaking) only defines a set of
index values, there needs to be a mapping between the set of index values an
index-based interval defines, and the source squence of elements.

* `s := (a, b, c, a, e)`
* `s[x]` is defined for `(x in [1,#s])`
* `i6 := [2, 4] => { 2, 3, 4 }`

Because of that, a sequence of index values must be formed first such that
it holds all the index values in the specified interval in ascending order.
Then, and only then can each index within that ordered sequence of intervals
be replaced by the symbol at the specified index whithin the source sequence.

* `( i6 := [2,4] ) => ( t := (2,3,4) ) => ( u := (b,c,a) )`

Note that the entire mapping needs to be understood to be defined in terms of
an operation/function over a given sequence and its index order. That operation
must also be understood to be defined to return a **substring** within the given
range of index values:

* `op(s,2,4) -> (b,c,a)`
* `s[a,b], s(a,b) := op(s,a,b)`

Note that, defined as above, both of the endpoints of the specified interval
are by definition included. It is therefore not possible to exclude any of
the endpoints. (This definition is however sufficient in the overall context
of this discussion).

<!-- ======================================================================= -->
## induced substrings

The interval `[a,b]` over a sequence `s` (i.e. `s[a,b]`) can be said to define
**an induced substring**. That is, given an interval and **a fixed set of rules**,
the resulting substring can be can be described as being induced by the input
interval and the following set of rules:

* from the input interval derive the set of index values
* based on these index values form an ordered sequence of index values
* within this sequence replace each index by the element of the source
  sequence that corresponds with the specified index/position

Note that this **interval-based perspective** on substrings over sequences of
elements does correspond with the first-to-last based perspective in regards
to sections. That is, the resulting induced substring of an interval-based
specification has a first and a last element, and contains every other element
in between.

<!-- ======================================================================= -->
## alternative, interval-based definitions

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

<!-- ======================================================================= -->
## remarks

Note that an index-based interval over a simple sequence may not necessarily
result in an ordered subsequence. That is, the resulting subsequences may still
contain elements multiple times. In contrary to that, an index-based interval
over an ordered sequence will always result in an ordered subsequence.

Note that a programming language does in general allow to specify substrings
via an offset and a length value. Such a specification does however still
translate to an index-based interval.

* `s[offset,length] <=> s[offset,(offset+length-1)]`
