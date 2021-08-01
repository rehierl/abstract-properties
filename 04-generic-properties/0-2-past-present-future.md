
<!-- ======================================================================= -->
# An analogy - a sequence of events

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
        current event | ---------> forward only
```

Given an infinte timeline with discrete timestamps, each of which can be assumed
to represent a certain event in time at which some implementation can access
information and execute one or more actions.

Based on that, one can imagine that the implementation travels from one point
in time to another in an orderly fashion, while processing the corresponding
events. That is, the implementation is understood to only travel forwards in
time, never backwards.

With that in mind, one can imagine that the implementation is paused at some
point in time, before it has started to process the corresponding event.

<!-- ======================================================================= -->
## past, present, future

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
          <---------- | ----------->
          past     present    future
```

The current event at which the implementation was paused `(n5)` can be described
as the implementation's **current present**. Similar to that, all the events
that are presequent to the current event `(*,n4]` can be understood to comprise
the **current past**. Likewise, all the events that are subsequent to the current
event `[n6,*)`, i.e. those that the implementation still has to process at some
point in the future, can be understood to comprise the **current future**.

<!-- ======================================================================= -->
## forward only

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
       |<------------>|
           cycles?
```

Since the implementation has already processed those events that are presequent
to the current event, one needs to see the events in `(*,n4]` as being "done".
That is, there is in general no reason as to why the implementation would want
to revisit those events.

However, even if the implementation wanted to travel back to some event in its
current past (e.g. `(n2)`), it would have to forget about all those events it
has already processed in between the current event `(n5)` and the event it
intends to travel back to (i.e. `[n3,n4]`). In some sense, the implementation
would have to be able to undo some of the actions it has already executed.

In general, such a "rewind" is possible for an implementation, but needlessly
difficult to clearly define and implement. One would therefore need solid
reasons as to why such a feature would have to be supported.

In addition to that, one would have to ensure that, once the past current event
`(n5)` is reached a second time, the implementation won't continue to jump back
to the past event. After all, an implementation must in general avoid to repeat
that cycles indefinitely since it would effectively "freeze" the implementation.

Because of that, a design that is expected to be in widespread use should not
include such processing steps since these make a design needlessly difficult
to communicate.

<!-- ======================================================================= -->
## knowledge based on past events

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
                      |<----------------->|
                           assume n9?
```

Similar to the issue with wanting to travel backwards in time is the issue about
being tempted to circumvent the lack of knowledge about future events. After all,
based on a given current event, an implementation has in principle no knowledge
of its current future.

In order to choose which actions an implementation has to execute knowledge is
required. That knowledge can however not build upon those events that are yet
to come. After all, these events have not yet been reached and are as such
unknown. An implementation can therefore only build upon the knowledge it has
gained from the current event and from past events.

Note that, if this "image" causes troubles because one assumes that the entire
document tree is in general always available, then one should think of an
implementation as being externally supplied with one node at a time. Based on
that, an implementation is in general not guaranteed to have the means to
simply "look ahead". Because of that, future events must always be considered
unavailable at the current present.

However, one could in general assume that, given a certain sequence of past
events, some specific future event might happen with some likelyhood. Based on
that assumption, one could be tempted to execute certain actions in the hopes
that the predicted event will eventually be reached at some point in the future.

The issue is however, that the predicted future event can not be guaranteed to
even exist. (In that regards, one just needs to think of user input errors).
With that in mind, and if the implementation would eventually be able to
detect that the event it predicted in the past wasn't actually encountered, the
implementation would then have to rewind to the event at which the prediction
was made. That in order to fix the inconsistent outcome.

In addition to that, who gets to decide which possible future events to support?
And at what point can such an event be considered to occur with a probability
that can be considered sufficiently high enough? That is, what is its threshold?
And will these classifications change over time (i.e. years? decades? centuries?)
based on some current fashion?

It is needless to state at this point, that a design that is expected to be
in widespread use over long periods of time should be independent of anyone's
personal preference.

<!-- ======================================================================= -->
## conclusions

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
          <-----------|------------>
          context   current    scope
```

Due to the above one can make the following statements in regards to what an
implementation can and can not do.

(**I1**) An implementation knows about past events. It can be assumed to know
which events occurred and which actions it took in response to these events.

(**I2**) An implementation knows about the current event. It can take the
knowledge it gained from the current event into account when deciding which
actions to take in response to the current event.

Note that the knowledge an implementation gained from past events, and the
actions it took in the past, including the knowledge it gained from the
current event, will in general be referred to as the implementation's
**(current) context**.

Note that the knowledge of the current event can be understood to introduce
some **reflexivity**. Based on that, certain actions may affect other actions
that are to be executed while processing the current event. This does for
example allow an implementation to associate a sectioning node with the
section it declares.

(**I3**) The actions an implementation chooses to execute in response to the
current event can only be taken into account when an implementation has to
decide which other actions to execute in response to the current event, and
when deciding which actions to execute in response to some future event.

Note that the amount of events that may take some action into account, can
be described as the action's **scope**. Since the current context does also
include the current event, the context of an implementation can be understood
to overlap with the scope of a current action in the current event.

(**I4**) Not every bit of knowledge gained from the current event and from
past events must be taken into account when deciding which actions to execute
in response to the current event. Put differently, an action taken in the
past may in general not required to have any effect on any of the future
events at all.

Note that I4 is not meant to express that an implementation can freely choose
which bits of information it chooses to use, and which it chooses to ignore.
After all, depending on its purpose an implementation is requried to follow
certain rules. Rules for example which tell that a certain section has ended.
