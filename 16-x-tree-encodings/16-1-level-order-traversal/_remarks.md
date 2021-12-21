
a level-order encoding (lvl-co)
- based on the level-order tree traversal
- must use group-ids in order to denote a child order

note that ..
- all child orders are substrings to the level-order trace
- compression - e.g. a sequence of (count,parent) intervals
- two numbers per non-empty child order

implicit encodings
- e.g. in terms of level values or scope sizes

grouping
- using group-ids as the elements in a sequence
  allows to group the actual elements, which
  can be identified by the corresponding index

sequences can be used to define trees (?)
- nested intervals - (f: Index -> Length)
- (a,b) = the pre-order trace of (a) has length (b)
- i.e. stretches over the next (b) nodes
- i.e. a length-based encoding

sequences can be used to define trees (?)
- node level/depth - (f: Index -> Level)
- (a,b) = node (a) is at node level (b)
- i.e. a level-based encoding
