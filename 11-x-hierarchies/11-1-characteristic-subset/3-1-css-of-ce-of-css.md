
<!-- ======================================================================= -->
## css-of-ce(), set-of-ce()

The CSS of a CE can be retrieved as follows:

```
css-of-ce(ce,S) begin
0: assert(ce in U(S))
1: T = { css(s) | (s in S) and (ce in css(s)) }
2: assert(#T > 0)
3: assert(#T < 1)
4: return oneOf(T)
end
```

Note that, since `(U == CE(S))` is true, input errors can easily be detected
by testing if the input CE is an element in `U`. Hence, if step-0 does not
trigger, then CE(S) can not be empty (i.e. step-2 won't trigger). And since a
CE is unique to its CSS, the overall result is uniquely defined (i.e. step-3
won't trigger) provided the setup is not broken.

```
set-of-ce(ce,S) begin
  css = css-of-ce(ce,S)
  s = set-of-css(css,S)
  return s
end
```

Note that, provided the input CE is an element in `U`, the result is defined
and unique. That is because the corresponding CSS can not be empty.

Note that neither `css-of-ce()` nor `set-of-ce()` allow to retrieve the empty
CSS of a parent set, or a parent set that has an empty CSS. None of those can
be retrieved as there is no CE that would allow to identify these sets.

<!-- ======================================================================= -->
## ce-of-css(), ce-of-set(), ce()

A (random) CE of any non-empty CSS can be retrieved as follows:

```
ce-of-css(css,S) begin
0: assert(css in CSS(S))
1: assert(#css > 0)
2: return oneOf(css)
end
```

Note that, provided the input CSS does indeed represent an element in `CSS(S)`,
the result is undefined if the CSS is empty. Furthermore, if the CSS has more
than one CE, the result is **a random CE** of the input CSS. That is because,
even though each CE is distinct to all the other CEs in that CSS, a simple set
of elements provides no means to retrieve a particular element (i.e. a CSS has
no first/last CE, etc). And even if a simple set of values had such means,
there is no information available to tell which specific CE to return.

```
ce-of-set(s,S) begin
  css = css-of-set(s,S)
  return ce-of-css(css,S)
end
```

Note that the result is either undefined (i.e. if `(css(s) == Ø)`),
the single CE of `css(s)`, or a random CE in `css(s)`.

```
ce(x,S) begin
  if (x in S) then
    //- recall (x in LS)
    return ce-of-css(x,S)
  else
    return ce-of-set(x,S)
  end if
end
```

Note that any leaf set is equal to its CSS (i.e. `(css(l) == l)`) and that the
CSS of a parent set is not an element in `P`. Hence, if parameter `x` is not a
set in `P`, then `x` must be a CSS. If, in contrary to that, `x` is a set in
`P`, then `x` may or may not be a CSS (i.e. leaf set vs. parent set).
