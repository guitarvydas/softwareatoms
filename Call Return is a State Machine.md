An XE that uses the `call` instruction, implicitly performs the following operations:
- *call*: own.state.resumePoint <- ...
- *call*: own.state.environment <- save registers (global  variables)
- *call*: allocate storage for parameter datums (on the global stack)
- *call*: GOTO callee (yield CPU)
- *resume*: restore registers <- own.state.environment
- *resume*: copy result value(s) <- from global stack or from global registers
- *resume*: execution point (PC) <- own.state.resumePoint
- *resume*: GOTO execution point (invoke self (unyield CPU))

# Simple Call Return State Machine
![[call-state-machine-Call Return (simple).svg]]

# Multi-Level Call Return State Machine
![[call-state-machine-Call Return (multi-level).svg]]