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