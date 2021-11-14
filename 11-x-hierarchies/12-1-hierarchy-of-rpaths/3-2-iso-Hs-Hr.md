
<!-- ======================================================================= -->
# hierarchy of rpaths <=> hierarchy of scopes

Even though one can first transform any hierarchy of rooted paths `Hr` into
a node tree `T(N,E)`, and then into a hierarchy of scopes `Hs`, one can also
directly transform `Hr` into `Hs`. Likewise, a direct transformation of `Hs`
into `Hr` is in principle possible.

<!-- ======================================================================= -->
## Hs => Hr

Recall that each set `(s in Hs)` in a hierarchy of scopes `Hs` has a unique
rooted path `rp(s)`. In addition to that, each set in `Hs` is required to have
one and only one CE which can be understood to denote the set's node id. Based
on that, `rp(s)` can be transformed such that each element in it is the CE of
the corresponding set. That is, the rooted path of each set in Hs can be
directly transformed into a rooted path of nodes.

* `Hr := { rpath(s) | (s in Hs) }`
* `rpath(s) := (ce(s1),..,ce(sN))` where `rp(s) := (s1,..,sN)`
* note - `rpath(s) == rp(n)` where `n := ce(s) := ce(sN)`

<!-- ======================================================================= -->
## Hr => Hs

```
rp(b) := (r  ..  a  ..  b)
         |-------|-------|
          rp(a)    p(a,b)
```

In order to transform Hr into Hs, one needs to recall the general pattern of
the rooted path of a node `b` that has node `a` as an ancestor. That is, each
rooted path `rp(b)` has the rooted paths of each of its ancestors `rp(a)` as
a prefix, and path `p(a,b)` as a suffix.

* `rp(b) := (rp(a) \ (a)) × p(a,b)`

Note that `rp(a)` and `p(a,b)` overlap each other in ancestor `a`.
That is, `(a)` is a suffix to `rp(a)` and a prefix to `p(a,b)`.

Due to the above, and in order to form the scope of node `a` from the rooted
paths in Hr, one first needs to restrict Hr to those paths that contain `a` as
an element. After that, all paths need to be reduced such that they all begin
in `a`. As such, `Hr(a)` can be understood to correspond with all the rooted
paths of the induced subtree that have node `a` as their root. The universal
set `U()` of `Hr(a)` is therefore equal to the scope of node `a`.

* `Hs := { U(Hr(a)) | (a in U(Hr)) }`

The following pseudocode fragment showcases a rudimentary direct approach.

```
produceHsFromHr(hr) begin
  hs = new set()

  foreach (a in U(hr)) begin
    //- ha is the scope of 'a'
    ha = new set()

    foreach (r in hr) begin
      ia = idx(r, a)

      //- ignore rooted path 'r',
      //  if 'a' is no node in it
      if(ia < 1) begin
        continue
      end

      for (i=ia; i<#r; i++) begin
        //- add each successor/descendant
        //  of 'a' in 'r' to 'ha'
        ha.add( r(i) )
      end
    end

    hs.add(ha)
  end

  return hs
end
```
