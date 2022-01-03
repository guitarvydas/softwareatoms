# The advantage to FP (Functional Programming)
- The advantage of FP is *not* that everything is a function.
- The advantage to FP is that everything is *explicit*.

# The Advantage of Being Explicit
- All forms of global variables are visible (made explicit), which, in essence makes them not global, but free.


# The Disadvantages of FP
- conflates xe's with data
- built-in operating system operations (blocking on Call until Return)
- hidden state (return address)
- over-specification (everything becomes synchronous, requires tricks to express asynchronous operations ("multitasking is hard" belief is due only to the application of the FP paradigm which is unsuited to multi-tasking))

# How Else to Achieve the Same Advantage?
- wires between boxes on a diagram - make each flow explicit (draw an explicit line for every datum flow) 
- supply an explicit parameter for each datum and for each callable function[^1]

[^1]: Note that FP programmers tend not to do this.  One supplies an explicit parameter for each passive datum, but one is allowed to call functions by name without having each function passed in as an explicit parameter.  First-class functions *allow* programmers to pass functions explicitly, but do not enforce this.  Allowing is not as good as encouraging! (Corollary: if *allowing* were good-enough, we would all be using assembler and GOTOs).  DLLs are a partial solution to this problem.  CPS is a partial solution to this problem (CPS tangles togeter passive and active data and does not encourage nesting - i.e. CPS is just a GOTO)