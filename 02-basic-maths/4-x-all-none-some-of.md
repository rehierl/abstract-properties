
TODO
- all-of, none-of, some-of
- in regards to sets of elements
- point out the difficulty with some-of

TODO
- all-of, none-of, some-of in regards to the relationships between sets
- note the difference between this set based context and these qualifiers
  in regards to a section in the context of a document
- (a section vs. a document) and (a section vs. a section)
- first, how a section is embedded into a document
- then, how a hierarchy of sections is established

intervals and the some-of operator
- `[a,b] := ( [a,*) & (*,b] )`
- i did expect `[a,b]` to be equivalent to `[a,*) \ (*,b)`
- note - which it is not (!)
- still - some-of := all-of one set, but none of the other
