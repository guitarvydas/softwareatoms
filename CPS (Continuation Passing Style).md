CPS is
- GOTO
- spaghetti control flow
- sychronous data passing of inputs
- synchronous data passing of outputs

# Use-Case for CPS
CPS is a low-level operation that can be used to build programming language semantics, i.e. compilers, interpreters.

I call CPS *low level* because it essentially allows you to do *anything* (including shooting yourself in the foot).

Assembler programmers loved GOTO because it allowed them to do *anything*.

Only a very few assembler programmers could construct "structured" systems using GOTOs.  Most programmers produced spaghetti code that could not scale.

Likewise, CPS and FP bible-thumpers are the "assembler programmers" of the current era.  Their techniques allow them to have unrestricted access to program development.  The majority of programmers will, though, fail to produce scalable software.
