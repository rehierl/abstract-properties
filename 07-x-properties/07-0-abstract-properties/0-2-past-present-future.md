
<!-- ======================================================================= -->
# An analogy - a sequence of events

Note that the following introduces a concept which will be referred to
as the **past-present-future (PPF) principle**, or as the **PPF analogy**.

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
      current event ->[]---------> forward only
```

Given an infinte timeline with discrete timestamps, each of which is assumed
to represent a certain point/event in time at which some implementation can
access information and execute one or more actions.

Based on that, one can imagine that the implementation travels from one point
in time to another in an orderly fashion, while processing the corresponding
events. That is, the implementation is understood to only travel forwards in
time, never backwards.

With that in mind, one can imagine that the implementation is paused at some
point, before it has started to process the corresponding event.

<!-- ======================================================================= -->
## past, present, future

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
           <----------[]---------->
          past     present    future
```

The current event `n5` at which the implementation was paused can be described
as the implementation's **current present**. Similar to that, all the events
that are presequent to the current event `[*,n4]` can be understood to define
the **current past**. Likewise, all the events that are subsequent to the
current event `[n6,*]`, i.e. those events that the implementation still has
to process at some point in the future, can be understood to define the
**current future**.

<!-- ======================================================================= -->
## forward only

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
       |<-------------[]
           cycles?
```

Since the implementation has already processed those events that are presequent
to the current event, one needs to see the events in the current past as "done".
That is, there is in general no reason as to why the implementation would even
want to revisit these points in time.

However, even if the implementation wanted to travel back to some event in its
current past, e.g. `n2`, it would have to forget about all those events it has
already processed in between the current event `n5` and the event it intends to
travel back to, i.e. `[n3,n4]`. To some extent, the implementation would thus
need to have the means to undo some of the actions it has already executed.

In general, such a "rewind" might be possible for an implementation, but
needlessly difficult to clearly define and implement. In order to justify
the additional effort required, one would therefore need to have clear
reasons as to why such a feature would have to be supported.

In addition to that, one would have to ensure that, once the then past current
event `n5` is reached once more, the implementation won't repeat the decision
to jump back to `n2`. Because of that, a design must in general avoid to
introduce cycles that might force an implementation to endlessly repeat the
same decisions since this could effectively "freeze" any implementation.

A design that is developed to be in widespread use should therefore not include
such processing steps since these make it difficult to communicate and
implement/debug.

Just imagine - What search engine would want to implement a design that could
enable malicious authors to trap their web crawlers in an endless loop?

<!-- ======================================================================= -->
## knowledge gained from past events

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
```

In order to choose which actions an implementation has to execute at a current
present, knowledge is required. That knowledge can however not build upon those
events that are yet to come. After all, these events have not yet been reached
and can therefore not be guaranteed to be encountered some time in the future.
An implementation can therefore only build upon the knowledge it has gained
from the current event and from past events.

Note that, if this "image" causes troubles because one assumes that the entire
document tree is in general always available, then one should think of an
implementation as being externally supplied with one node at a time (i.e. as
an actual stream of nodes). Based on that, an implementation is in general not
guaranteed to have the means to simply "look ahead". Because of that, future
events must always be considered unavailable at any current present.

<!-- ======================================================================= -->
## assume some future event?

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
|-------------------->[]----------------->|
 knowledge thus far    assume that n9 exists?
```

Similar to the issue of wanting to travel back in time is the issue of being
tempted to circumvent the lack of knowledge about future events. That is, one
could in general assume that, given a certain sequence of past events, some
specific future event might happen with some likelyhood. Based on that, one
could be tempted to execute certain actions in the hopes that the predicted
event will eventually be reached at some point in the future.

The issue with that is however, that the predicted future event can not be
guaranteed to exist. (In that regards, one just needs to think of user input
errors). With that in mind, and if the implementation would eventually be able
to detect that the event it predicted some time in the past wasn't actually
encountered, the implementation would then have to rewind to the event at which
the prediction was made. After all, the prediction made will have had an impact
on subsequent decisions. Because of that, a "rewind" must be performed in order
to "fix" the inconsistent outcome.

In addition to that, who gets to decide which possible future events to support?
And at what point can such an event be considered to be sufficiently "probable"?
That is, what is the threshold of such a probability, and will the classification
change over time (i.e. after years, decades?) based on some fashion?

It is needless to state at this point, that a design that is developed to be
in widespread use over long periods of time must be independent of anyone's
personal preference.

<!-- ======================================================================= -->
## conclusions

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
          <-----------[]----------->
          context   current    scope
```

Based on the above one can make the following statements in regards to what
an implementation can and can not do.

(**I1**) An implementation knows about past events. It can be assumed to know
which events it has already encountered, and which actions it took in response
to these events.

(**I2**) An implementation knows about the current event. It can take the
knowledge it gains from the current event into account when deciding which
actions to take in response to that current event.

Note that the knowledge an implementation gained from past events, and the
actions it took in the past, including the knowledge it gained from the
current event, will in general be referred to as the implementation's
**(current) context**.

Note that the knowledge of the current event can be understood to introduce
some **reflexivity**. That is, certain actions may affect other actions that
are still to be executed while processing the current event. This does for
example allow an implementation to associate a sectioning node with the
section it declares.

(**I3**) The actions an implementation chooses to execute in response to the
current event can only be taken into account when an implementation has to
decide which other actions to execute in response to the current event, and
when deciding which actions to execute in response to some future event.

Note that the amount of events that may take an action into account, can be
described as the action's **scope**.

Note that, since the current context does also include the current event, the
context of an implementation can be understood to **overlap** with the scope
of a current action in the current event. That is, an event is understood to
be an element in its context and also an element in its scope.

Note that this is similar to rooted paths and induced subtrees in a node tree.
That is, the rooted path of a node `n` ends in that node. Also, the induced
subtree `t[n]` has that node as its root.

(**I4**) Not every bit of knowledge gained from the current event and from
past events must be taken into account when deciding which actions to execute
in response to the current event. Put differently, an action taken in the past
is not required to have any effect on any of the future event at all.

Note that this can be understood to allow to "override" past decisions based
on all the information that is available in some future current context.

Note that I4 is not meant to express that an implementation can freely choose
which bits of information it chooses to use, and which it chooses to ignore.
After all, depending on its purpose an implementation is requried to follow
certain rules. This to guarantee that different implementations produce the
same results based on the same input.
