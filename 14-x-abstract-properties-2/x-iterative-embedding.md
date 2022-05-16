
- recall the iterative process of embedding child orders
- which will result in the document tree's pre-order trace

```
  step-1   step-2    step-3    step-4    step-5    step-6    step-7
| ====== | ======= | ======= | ======= | ======= | ======= | ====== |
| r      |  r      |  r      |  r      |  r      |  r      |  r     |
| |-->|  |  a      |  a      |  a      |  a      |  a      |  a     |
| a  s3  |  |      |  p      |  p      |  p      |  p      |  p     |
| |      |  |-->|  |  |-->|  |  n      |  n      |  n      |  n     |
| |-->|  |  p  s3  |  n  s3  |  |-->|  |  d      |  d      |  d     |
| p  s2  |  |      |  |      |  d  s3  |  |-->|  |  s1     |  s1    |
| |      |  |-->|  |  |-->|  |  |      |  s1 s3  |  |-->|  |  s2    |
| |-->|  |  n  s2  |  d  s2  |  |-->|  |  s2     |  s2 s3  |  s3    |
| n  s1  |  |      |  |      |  s1 s2  |         |         |        |
| |      |  |-->|  |  s1     |         |         |         |        |
| d      |  d  s1  |         |         |         |         |        |
|        |         |         |         |         |         |        |
|-phase-1----------------------------->|-phase-2------------------->|
```

- note that siblings are pushed downwards with each iteration
- step-1 to step-3 will extend the scope of node n
- step-5 to step-7 will only transform the scopes into substrings

hence - "scope-x" to denote the scope over the tree order that results
from embedding the x-th child order.

```
<r> <a> <p> <n> <d/> </n> <s1/> </p> <s2/> </a> <s3/> </r>
            |-scope-4/5/6/7------------------------>|--->|
            |-scope-3------------------->|--->|
            |-scope-2-------->|--->|
            |-scope-1-->|
            |-| scope-0
```

- even though the scope of a node ends with a particular last node
- the generic definition must be based on the end-tag of its ancestor

based on the iterative process ..
- scopes can in general be defined in terms of **the n-th iteration**
- including the embedding of the edges of the unordered document tree (?)

however
- there is no unique definition for the scope over the pre-order trace
- it can be based on any number of iterations - i.e. unclear

```
<r> <a> <p> <n> <d/> </n> <s1/> </p> <s2/> </a> <s3/> </r>
            |-scope-N(+1/2/*)---------------------->|--->|
            |-scope-*------------------->|--->|
            |-scope-2-------->|--->|
            |-scope-1-->|
            |-| scope-0
```

- the scope over the pre-order trace is the result of ..
- the N-th iteration up to and including the last iteration

note
- (N) can not be some specific number since ..
- node (n) may have any number of ancestors

just to add insult to injury
- N is in general different for distinct nodes
- may be X for one node and Y for another - where (X != Y)

one can in general only state that ..
the scope over the document tree's pre-order trace is the scope that results
from **the last iteration** (i.e. type-N). that "definition" is however, in
contrary to scope-0, scope-1 and scope-2, arbitrary, and therefore
**remains unclear**.
