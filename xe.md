An eXecutable element has
- an input queue
- an output queue.

# Suggestion - Tagged Messages
I suggest that messages to/from xe's be tagged with a string/number.

Otherwise, messages are defined by their order.

I.E. I suggest that a message is:
- a tag
- data.

Whereas an untagged message is:
- data.


## Analogy: Ordered Parameters vs. Named Parameters

Using functions, we can specify:

- fn(x,y), or,
- fn(a=x,b=y).

In the first case, the order of the parameters matters.  The call-point syntax defines which parameter "x" will be bound to and which "y" will be bound to.

In the second case, the order of the parameters does not matter.  The call-point syntax defines the bindings ("x" is bound to "a" and "y" is bound to "b").

We can rewrite the second case as:

- fn(b=y,a=x)

with no change in meaning, but, if we rewrite the first case as:

- fn(y,x)

the actual bindings are different.