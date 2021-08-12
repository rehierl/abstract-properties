
<!-- ======================================================================= -->
# functions

A function `(f: A -> B)` is a binary relation between two sets such that each
element of the 1st set `A` (its **domain**) is mapped onto exactly one element
of the 2nd set `B` (its **codomain**).

* `y = f(x)` for `(y in B)` and `(x in A)`
* `R(f) := (A,B,G)` where `G := { (x,f(x)) | (x in A) }`
* any function is required to be **left-total**
* any function is required to be **right-unique**

<!-- ======================================================================= -->
## injective, surjective, bijective

A function that is **also left-unique** is said to be **injective**. (aka.
a **one-to-one** function). That is, each element `(x in A)` is mapped onto
a unique element `(y in B)`. Loosely described, no two distinct elements
have the same "outcome".

* injective := if `xRy` and `zRy`, then `(a == b)`

A function that is **also right-total** is said to be **surjective** (aka.
an **onto** function). That is, for each `(y in B)` there is a `(x in A)`
such that `(f(x) == y)`. Loosely described, each `(y in B)` is the "outcome"
of some `(x in A)`.

* surjective := for any `(y in B)` there is an `(x in A)` such that `xRy`

Note that a relation that is left- and right-unique can be described as
a relation that is **unique**. Any injective function therefore corresponds
with a relation that is unique.

Note that a relation which is left- and right-total can be described as
**total**. Hence, a surjective function can be described as total.

A function that is **also injective and surjective** (i.e. unique and total)
is said to be **bijective**.  As such, it can be referred to as
**a one-to-one correspondence**.

<!-- ======================================================================= -->
## inverse functions

Any bijective function `(f: A -> B)` has an inverse function `(g: B -> A)`
such that `(g(y) == x)` iff `(f(x) == y)`. A function that has an inverse
can be described as **invertible** or **reversible**.

Loosely described, the inverse `g` reverses the outcome of `f`.

* `R(g) := (B,A,G)` where `G := { (f(x),x) | (x in A) }`
* note - the orientation of each edge is "flipped"

remarks

* `(f(x) == y) <-> (g(y) == x)`
* `(g(f(x)) == x)` and `(f(g(y)) == y)`
* `f° := g` - i.e. `°` may be used to denote the inverse to `f`

Note that an inverse function is also required to be a function and therefore
also required to be left-total and right-unique. Consequently, for an inverse
function `g` to exist, function `f` must also be right-total and left-unique
and is therefore require to be bijective.

<!-- ======================================================================= -->
## monotone functions

A function that maps elements from a domain, which are larger than previous
ones, onto elements in the codomain, that are larger than the previous result,
is said to be **monotone increasing** or **order-preserving**.

* monotone increasing := if `(a <= b)`, then `(f(a) <= f(b))`
* strictly increasing := if `(a < b)`, then `(f(a) < f(b))`

A function that maps elements from a domain, which are larger than previous
ones, onto elements in the codomain, that are smaller than the previous result,
is said to be **monotone decreasing** or **order-reversing**.

* monotone decreasing := if `(a <= b)`, then `(f(a) >= f(b))`
* strictly decreasing := if `(a < b)`, then `(f(a) > f(b))`

A function is **strictly (montotone) increasing/decreasing** iff the elements
involved are all distinct - i.e. `(<)` and `(>)` instead of `(<=)` and `(>=)`.
A function is **strictly montonic**, if it is strictly increasing or strictly
decreasing.
