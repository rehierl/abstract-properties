
<!-- ======================================================================= -->
## concatenation - (×)

```
concatenate(s, t) begin
  u = ()
  for i=1 to #s begin
    v = s(i)
    u.append(v)
  end
  for j=1 to #t begin
    v = s(j)
    u.append(v)
  end
  return u
end
```

While the subset-of operation is most natural (read "most natural" as in
"most used") in regards to simple sets, that isn't the case in regards to
sequences and their subsequence-of operation. More "natural" in regards to
sequences is the concatenation based operation.

* `(s × t), (s concat t) := concatenate(s, t)`

<!-- ======================================================================= -->
## substring-of, prefix, infix, suffix

A sequence `t` can be described as a substring in regards to a sequence
`x`, if `x` can be formed via the concatenation of three sequences.
Because of that, `x` can be described as a **super-string** to sequence `t`.

* `substring-of(x, t) := (x == (s × t × u))`

Note that any of these sequences may be the empty (i.e. `()` or `Ø`).
In addition to that, `s` may be referred to as a **prefix**, `t` as an
**infix** and `u` as a **suffix** to `x`.

Note that any sequence is a substring to itself. Furthermore, prefix `s`
and suffix `u` are also substrings to `x`.

Note that, the substring-of() operator can also be understood from
**a removal-based perspective**. That is, sequence `t` is a substring to
sequence `x`, if `t` can be formed by removing some prefix `s` and/or some
suffix `u` from sequence `x`.

Note that it is at this point non-relevant if the super-string contains the
pattern of a sub-string more than once. The substring's "multiplicity" in
regards to its super-string may be greater than one. That is, a substring may
have more than one offset within a given super-string.

Similar to simple sets, the equal() operator can also be defined based upon
concatenation. That is, two sequences are considered equal, if both are
substrings to each other.

* `(s == t) := (s substring-of t) and (t substring-of s)`

<!-- ======================================================================= -->
## strict/proper-substring-of

Substring `s` can be described as **a strict substring** of sequence `t`, if
`t` has one or more additional elements as a prefix and/or suffix to `s`.

* `(s strict-substring-of t) := (s substring-of t) and (s != t)`
* `(s strict-substring-of t) -> (#s < #t)`

A (strict) substring is considered **sub-ordinate** (in regards to its length)
to a superset. Conversely, a super-string is considered to be **super-ordinate**
to a substring.

<!-- ======================================================================= -->
## (strictly) related

Two sequences are said to be related with each other, if one is a substring
of/to the other. In addition to that, two distinct related strings can be
clarified as strictly related strings.

* `(s related-to t) := (s substring-of t) or (t substring-of s)`
* `(s strictly-related-to t) := (s related-to t) and (s != t)`

As before, this related-to operator can also be understood to be based upon
a clear defintion. That is, if **all-of** is understood to be in regards to
a substring is contained **as-is** within its superstring.

Note that this definition of the related-to operator heavily relies upon one
sequence containing the other sequence as-is. Hence, and if defined based upon
the substring-of operator, the related-to operator can be clarified as being
"strict".

<!-- ======================================================================= -->
## overlap

Two sequences can be described as overlapping each other, if both can be formed
from a non-empty prefix and suffix, and if the prefix of one is equal to the
suffix of the other.

* `s := (t × u)` and `x := (y × z)`
* `(x overlaps y) := ( (u == y) or (t == z) ) and (t,u,y,z != Ø)`
