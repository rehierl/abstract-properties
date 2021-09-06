
# preD

* `preD(n) := n × (fc .. lc ..)`
* `trace(n) := n × trace(fc) × ... × trace(lc)`
* `tags(n) := (<n attrib*>, fc, .., lc, .., </n>)`
* no order of execution required
* a hierarchy of scopes, interleaved child orders
* order-preserving, reverse to `postR`

# levelD

* `lvlD(n) := n × (ns .. ls) × (fc .. lc)`
* `tags(T) := (.., <tag p="r">, fc, .., lc, </tag>, ..)`
* must begin with the tree's root,
  continue with its child order, ..
* non-hierarchical, a sequence of child orders
* order-preserving

# preR

* `preR(n) := n × (lc .. fc ..)`
* `trace(n) := n × trace(lc) × ... × trace(fc)`
* `tags(n) := (<n attrib*>, lc, .., fc, .., </n>)`
* no order of execution required
* a hierarchy of scopes, interleaved child orders
* not order-preserving, reverse to `postD`

# postD

* `postD(n) := (.. fc .. lc) × n`
* `trace(n) := trace(fc) × ... × trace(lc) × n`
* `tags(n) := (<n>, .., fc, .., lc, </n attrib*>)`
* no order of execution required
* a hierarchy of scopes, interleaved child orders
* not order-preserving, reverse to `preR`

# postR

* `postR(n) := (.. lc .. fc) × n`
* `trace(n) := trace(lc) × ... × trace(fc) × n`
* `tags(n) := (<n>, .., lc, .., fc, </n attrib*>)`
* no order of execution required
* a hierarchy of scopes, interleaved child orders
* order-reversing, reverse to `preD`
