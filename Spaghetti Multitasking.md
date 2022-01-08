Ostensibly, operating systems are meant to implement multitasking.

Operating systems invoke (resume) processes and block processes.

Call/return, e.g. `fn(x)`, performs blocking and, therefore, subsumes some of the functionality thought to belong only to operating systems.

Furthermore, call/return is implemented as state machines.

I argue, therefore, that blocking is not nested (localized) and results in spaghetti programming, much like the use of GOTO before the advent of *Structured Programming*.

In this article, I further discuss blocking and how operating systems wrest blocking control away from function-based programs.

# eXecutable Elements
Data on a computer comes in 2 forms:
- a datum
- a executable datum - an XE (eXecutable Element).

An XE is like a *function* in popular progamming languages, but, without
- parameters
- return values
- return address (state).

An XE  contains computer instructions.  

On present hardware, XEs are stored in memory and the computer instructions are in the form of bytes/words/longwords/etc. in that memory.

In some computer architectures, XE memory is separated from datum memory by hardware.  In such cases, a hardware *trap* (exception, interrupt) is raised if any attempt to invoked instructions that are not in memory reserved exclusively for XEs.

# Invoking
An XE is invoked - given life - by the operating system.

It is easiest to imagine an XE situated on a single-cpu (single-thread) system.  In such a case, an XE is brought to life by assigning the CPU (thread) to executing the code contained in the XE.  The Dispatcher (aka Operating System) ostensibly decides which XE gets to use the CPU (thread), leaving all other XEs without threads (lifeless).

# Blocking
A XE is `blocked` if it gives up the use of the CPU (thread).

In popular languages blocking occurs in at least these ways:
- An XE finishes its work and "returns" the use of the CPU to the Dispatcher.
- An XE `yields` the CPU back to the Dispatcher.  The XE expects to resume its work, later.  The Dispatcher determines the meaning of "later".  Note that, in this case the XE or the Dispatcher must store state information about the XE so that the XE can resume its work.  This state information is often called a `return address` and is most often implemented using the CPU's PC register.
- An XE `yields` the CPU to another XE by using the `call` instruction.
- An XE `yields` the CPU to the calling XE by using the `return` instruction.

## The Cost of Blocking


# Blocking Spaghetti
Note that the decision to `invoke` an XE is made by totally different programs - the Dispatcher (aka Operating System) and any XE that uses the `call` or `return` instructions.

Note that the programs are not necessarily nested or localized.  

This conflation or responsibility results in what was once called `spaghetti programming`.

# Preemption
Operating systems are designed to have priority over scheduling decisions, i.e. decisions about blocking.

Since XEs can block without informing the Scheduler (XEs using the `call` and `return` instructions directly), Operating Systems must take extreme measures to wrest control away from XEs.

These extreme measures are often called `preemption`.

`Preemption` would be unnecessary if XEs dis not have the ability to circumvent blocking decisions.


# Mutual Multitasking
Early attempts at using preemption-less operating systems, e.g. Windows 3.x, ended in failure.

This failure was not due to the preemption-less nature of these attempts, but was due, IMO, to spaghetti architecture - the inability to segregate required functionality (aka `divide and conquer`).

In this particular instance, the programs called `operating systems` needed to solve two completely different problems:
1. scheduling and invoking XEs
2. protecting individual XE memory space from other XEs.

Note that only a few programs are intended to solve these very same problems (e.g. Linux, MacOS, Windows), yet, all of our programs, today, pay the cost of solving this problem.

# Preemption-Less Programming
Modern hardware provides support for solving the problem separating XE memories from one another.

The concept of preemption-less programming has been ignored, because it was thought to be involved only with Operating System program design.

# Composition
You can't compose programs unless their effects are totally isolated from one another.

So-called `encapsulation` is not enough.

`Encapsulation` in popular languages (e.g. OO (Object Oriented)) affects only data, but not XE threads of execution.

# First-Class Functions, Closures, etc.


# What is Enabled?
diagrammatic programming, e.g. box-and-arrow programming
build-and-forget
true isolation
DSLs - e.g. parsing, Ohm-JS, prep