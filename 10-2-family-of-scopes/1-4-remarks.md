
<!-- ======================================================================= -->
## a visual impression

Assuming a **partial setup (T1)** `S` ..

```
|-S----------------------------------------|
|                               |-D(s)---| |
| |-A(s)---------------|        | |-> .. | |
| | r(s) -> .. -> p(s) | -> s ->|-|->    | |
| |--------------------|        | |-> .. | |
|                               |--------| |
|------------------------------------------|
```

* for `(s in S)` ..
* `A(s)` is a total sub-setup
* `r(s)` is equal to `max(A(s))`
* `p(s)` is equal to `min(A(s))`
* `D(s)` is a partial sub-setup

<!-- ======================================================================= -->
## remarks - total (sub)setup

Note that `A(s)` is always a total sub-setup. Because of that, any non-root
set `(s in S)` always has a most significant `r(s) := max(A(s))` and a least
significant `p(s) := min(A(s))` **superset**.

* `(r(s) == p(s))` for `(s in c(r))` and `(r in RS)`

Note that each parent set in a total setup always has **one child set only**.
( That is because if a parent set had more than one child set, then the setup
would have a pair of unrelated sets. As such, the setup would not be a total
setup ). Consequently, each parent set in a total setup always has a least
`l(p)` and a most significant **subset** `c(p)`. Any non-empty total setup
therefore has **one root and one leaf set only**.

<!-- ======================================================================= -->
## remarks - partial (sub)setup

Note that `D(s)` is in general a partial sub-setup. Because of that, there
is no least/most significant subset in it. However, the set of all leaf
sets `l(s)` can be described as the set of all **minimal subsets** and
the set of all child sets `c(s)` can be described as the set of all
**maximal subsets**. Conversely,
