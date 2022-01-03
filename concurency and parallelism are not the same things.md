Concurrency is a way to write code.  A paradigm.

Parallelism is an optimization that *can* be applied to concurrent code.

One can write concurrent code without parallelizing the code.

One cannot write parallel code without making the code concurrent[^1].

[^1]: You can try to write parallel code without making the code concurrent, but this usually results in bugs.

# The Concurrent Paradigm
- code that assumes nothing about its inputs nor outputs
- code that "call" other code (it can only yield to the Dispatcher)
- does not take parameters (but, you can Send data to it)
- does not return values (but, it can Send data to any Receiver)
- has an input queue (receives tagged messages)
- has an output queue (enqueues tagged messages)

## Counter-Example
A function call, such as `f(x,y) -> z` is not concurrent.

It is built up of these operations:
- Dispatcher: Send(x) to f
- Dispatcher: Send (y) to f
- Dispatcher: invoke f
- f: GOTO own.state
- f: deal with data x and y
- f: Send (z) to own output
- f: own.state = return address (another xe?)
- f: yield to Dispatcher

## Example - Data Collection Server
xe: GOTO own.state
xe: deal with input, change own.env
xe: (Send nothing)
xe: own.state = ...
xe: yield to Dispatcher

## Example - HTML Server
xe: GOTO own.state
xe: Send (html page) to own.output
