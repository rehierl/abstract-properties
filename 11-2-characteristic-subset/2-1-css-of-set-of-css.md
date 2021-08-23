
<!-- ======================================================================= -->
# the parent set s of css(s)

Since any set `(s in S)` is a proper subset to its ancestors `(a in A(s))`,
and since `s` is a superset to `css(s)`, set `s` is the least significant
superset to `css(s)` in `A*`. As such, set `s` can be described as
**the parent set of css(s)**.

* `A(s) := { a | (a ancestor-of s) }`
* `A*(s) := (A(s) + {s})`

Note that, a non-empty `css(s)` can be described as "unique" since `(s in S)`
can be uniquely identified. After all, `s` is the least significant set in
`S` to which `css(s)` is still a subset.

<!-- ======================================================================= -->
## css-of-set(), css()

As a matter of completeness, `css(s)` can be implemented as follows:

```
css-of-set(s,S) begin
  css = clone(s)
  for each (c in c(s)) begin
    if (c subset-of css) then
      css = css \ c
    end
  end if
  return css
end
```

<!-- ======================================================================= -->
## set-of-css()

The parent set `(s in S)` of `css(s)` can be identified as follows:

```
set-of-css(css,S) begin
1: T = < s | (css(s) == css) for (s in S) >
2: assert(#T > 0)
3: assert(#T < 2)
4: return oneOf(T)
end
```

The possible outcomes are:

(0) The result is undefined, if no `(s in S)`
exists such that `(css(s) == css)` - i.e. trigger step-2.

Note that this step represents an user input error.

(1) If the input argument `css` is empty,
and if step-2 did not trigger, then ...

(1.1) The result is unclear if more than one `(p in PS)`
exists such that `(css(p) == Ø)` - i.e. trigger step-3.

(1.2) The result is `p`, if exactly one `(p in PS)`
exists such that `(css(p) == Ø)`.

(2) If the input argument `css` is non-empty,
and if step-2 did not trigger, then ...

(2.1) The result is a unique `(s in S)`.
That is because each non-empty CSS is unique to its parent set.

<!-- ======================================================================= -->
## remarks

Note that each non-empty setup always has at least one non-empty CSS.
That is because each such setup must have at least one leaf set.

Note that there is only one case possible (i.e. case-1.1) such that no unique
result can be returned, even though the input argument `css` is valid (i.e.
no input error). In contrary to that, the result in case-2.1 is unique since
no two sets can have the same non-empty CSS.

Note that, since no setup may contain the empty set (i.e. `(Ø not-in S)`),
the empty set `Ø` could be returned to indicate an error case.

<!-- ======================================================================= -->
## remarks

The result of `set-of-css(css,S)` is **defined and unique**
for any `css`, if the following requirements are met:

* `(css in CSS(S))` is true - i.e. no input error
* `( #{ s | (css(s) == Ø) for any (s in PS) } <= 1)`
* note - no more than one parent set has an empty CSS

Note that `set-of-css()` is then inverse to `css()`.

* `(set-of-css(css(s)) == s)` is true for any `(s in S)`
* `(css(set-of-css(css)) == css)` is true for any `(css in CSS(S)`
