
# doctree order

- this chapter tries to join the following aspects:
  pre-order tree traversal, tag soup, document order

tag soup
- a tag soup can be seen as a sequence of enter- and exit-events
- each enter-event is paired with a subsequent exit-event
- produced by a combination of the pre-order and post-order traversals

pre-order traversal
- the enter-order corresponds with the pre-order visit order
- each start-tag corresponds with the visit of a node
- each start-tag denotes the absolute position of a node
- the document order is the pre-order node order
- each start-tag also denotes the start of the node's scope
- in contrary to that, each end-tag (only) denotes the end of the node's scope

* start-tag <=> enter a node's scope and visit that node
* end-tag <=> only exit the node's scope

consequences which result from that
- (1) a tag soup ain't no node tree
- (2) well-formedness is a must, DI-RE
- (3) associate while visiting/entering

# todo
