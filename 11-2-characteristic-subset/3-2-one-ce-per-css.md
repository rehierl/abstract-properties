
<!-- ======================================================================= -->
## Iff (#CE(s) == 1)

```
|----------------|
| s1    s2    s3 | - S
|-|-----|-----|--|
  |     |     |
|-|-----|-----|--|
| c1    c2    c3 | - CSS(S)
|-|-----|-----|--|
  |     |     |
|-|-----|-----|--|
| e1    e2    e3 | - CE(S)
|----------------|
```

The following is true, iff each CSS has exactly one CE:

* if `(#CE(s) == 1)` is true for each `(s in S)`, then ...
* `ce-of-set()` is defined and unique for every `(s in S)`
* `set-of-ce()` allows to reliably retrieve each `(s in S)`

If each CSS has exactly one CE (i.e. `(#css(s) == 1)`), then
`U` and `S` have the same number of elements (i.e. `(#U == #S)`).

(1) `(#CSS(S) == #S)` is true.
That is because each set `(s in S)` has a unique non-empty CSS

(2) `(#CE(S) == #CSS(S))` is true.
That is because each CSS is required to have exactly one CE.

(3) `(#U == #S)` is true.
That is because `(#U == #CE(S) == #CSS(S) == #S)`.

* `(#U == #S)` is true, iff `(#CE(s) == 1)`

Due to the above `ce-of-set()` is then **inverse** to `set-of-ce()`.

* `(set-of-ce( ce-of-set(s) ) == s)` is true for each `(s in S)`
* `(ce-of-set( set-of-ce(ce) ) == ce)` is true for each `(ce in CE(S))`
