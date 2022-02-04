
# a little bit of private history ...

This repository is overall a complete rework of the **node-tree-outliner**
(archived) and several other repositories (public and non-public) I had
created on the HTML outliner issue.

* 2017-06 to 2017-07 - html-outliner-impl - A failed attempt to implement the
  official outline algorithm using JavaScript.
* 2017-06 to 2018-01 - html-outliner-spec - An analytical approach to translate
  the official specification into pseudocode, which made several formal issues
  in the official design painly obvious.
* 2017-07 to 2019-04 - node-tree-outliner - In essence my first attempt to
  grasp the underlying mathematical aspects one needs to be aware of when
  trying to develop a consistent alternative. Unfortunately, at that time,
  I was however still unable to reach the level of abstraction that is
  required to see the forest amongst all those trees.
* 2019-04 to 2019-05 - ordered-trees - This non-public repository more or less
  reflects a transition from a graph-based point to an order-based point of
  view. That is, I did start to realize that "ordered trees" don't actually
  exist. This realization did eventually open my eyes to an interval-based
  point of view on scopes, and eventually to abstract properties.
* in 2019-08 - archived my online repositories
* in 2019-08 - brainstorming-notes (private) - In essence a summary of the
  off-topic notes I had accumulated over the time. Mostly taken from the
  repositories mentioned above.
* 2021-07 to 2022-01, and counting - abstract-properties - This repository
  does in essence provide a consistent foundation in terms of a concept of
  abstract properties whose scopes can be described as open intervals over
  the appropriate base order, linear or otherwise.

So yes, I have already managed to waste several years of my life trying to
figure out how to explain the mathematical aspects related to HTML's
unresolved outliner issue, initially without even realizing that something
like [Order Theory (OT)](https://en.wikipedia.org/wiki/Order_theory) could
already exist ...
