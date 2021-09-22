
```
      subsequent           presequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (ls .. ns) -> n -|-> (ps .. fs)   |  n -|-> (ps .. fs)      |  n -|-> sR
                       |-> (lc .. fc)   |     |-> (lc .. fc)      |     |-> cR
                                        |                         |
                           child nodes  |                         |
```

general impression
- we are overly used to total orders
- we are barely aware of partial orders

context rooted paths
- the last node of a property is subsequent to its
  defining node, because of that, the defining node
  is a node in the last node's rooted path
- a matter of consequence

rank-based sections
- use the total document order to introduce rank-based sections
- allows to explain how a node order can be broken apart

html headings
- introduce the h-element as a DTO scoped heading?
- i.e. and leave the others as broken DPR headings?
- no - that would be a fucking mess of scopes
- all headings must be DTO headings
- and the h-element is the only rank-less heading
