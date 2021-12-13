
<!-- ======================================================================= -->
# hierarchy of rscopes (Hrs) <=> hierarchy of scopes (Hs)

Even though one can first transform a hierarchy of reversed scopes Hrs into a
node tree `T(N,E)`, and then that tree into a hierarchy of scopes Hs, a direct
transformation of Hrs into Hs is possible. Likewise, a direct transformation
of Hs into Hrs is possible.

<!-- ======================================================================= -->
## (Hs => Hrs)

Recall that each set `(s in Hs)` in a hierarchy of scopes `Hs` has a unique
rooted path `rp(s)`. In addition to that, each set in `Hs` is required to have
one and only one CE, which can be understood to denote the node a set represents.
Because of that, `rp(s)` can be transformed such that each element in it is the
CE of the corresponding scope. That is, the rooted path of each set in Hs can
be transformed into a rooted path of nodes. That rooted path of nodes can then
be used to form the reversed scope of the defining node.

* `RPs := { rp(s) | (s in Hs) }`
* `replace(p): (s1..sk) -> (ce(s1)..ce(sk))`
* `Hrp := { replace(p) | (p in RPs) }`
* `Hrs := { N(p) | (p in Hrp) }`

<!-- ======================================================================= -->
## (Hrs => Hs)

```
rp(b) := (r  ..  a  ..  b)
         |-------|-------|
          rp(a)   p(a,b)
```

As before with a hierarchy of rooted paths Hrp, one needs to recall the general
structure of a rooted path, each of which has the rooted paths of its ancestors
as a prefix. Since a hierarchy is always downward-total, the rooted paths of
elements `a` and `b` can be used to form the path `p(a,b)` that connects both
of these elements.

* `p(a,b) := (a) × (rp(b) \ rp(a))`

With that in mind, and in order to form the scope of node `a` from the reversed
scopes in Hrs, one first needs to restrict Hrs to those reversed scopes that
have node `a` as an element. After all, the rooted paths of all the descendants
of that node have the rooted path `rp(a)` as a prefix, which in this context
is a subset to the corresponding reversed scopes. As such, the universal set
of elements `U()` of `Hrs(a)` contains all the ancestors of node `a` and also
all the nodes in the induced subtree `T[a]`. Because of that, removing all the
nodes in `A(a)` from `U()` will yield the scope `s(a)` of that node.

* `Hrs(a) := { s | (a in s) for (s in Hrs) }`
* `s(a) := ( U(Hrs(a)) \ rs(a) ) + {a}`

Recall that the reversed scope `rs(a)` is that scope, which has `a` as its
characteristic element. Because of that, `rs(a)` is the most significant
reversed scope in `Hrs` (i.e. least amount of elements) that has `a` as an
element.

<!-- ======================================================================= -->
## (Hrs => Hs) in pseudocode

The following pseudocode showcases a rudimentary implementation.

```js
getHsFromHrs(hr) begin
  //- the resulting hierarchy of scopes
  hs = new set()

  foreach (a in U(hr)) begin
    //- initialize the scope of node `a`
    sa = new set()
    ra = null

    foreach (rs in hr)  begin
      //- if 'a' is no element in the current
      //  reversed scope, then node 'a' is no
      //  ancestor to any node in that scope
      //- that reversed scope can be ignored
      if (a not in rs) begin
        continue
      end

      //- add the nodes in this reversed scope
      //- at this point we do not know which
      //  of these nodes are descendants to 'a'
      foreach (n in rs) begin
        sa.add( n )
      end

      //- we need to detect and remember
      //  the reversed scope of node 'a'
      //- since ra is then equal to A*(a)
      if (ra == null) or (rs.size < ra.size) begin
        ra = rs
      end
    end

    //- 'sa' contains all the nodes in A(a)
    //  and also all the nodes in T[a]
    //- remove all the nodes in A*(a)
    foreach (n in ra) begin
      sa.remove( n )
    end

    //- need to re-add 'a' since 'a'
    //  A*(a) and also in T[a] (= D*(a) )
    sa.add( a )
    hs.add( sa )
  end

  return hs
end
```
