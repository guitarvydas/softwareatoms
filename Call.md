alloc data
send data to proc
retaddr <-- label
goto proc
label:

In typical language with typical compilers on typical CPUs
1. "alloc data" is done by pushing data onto a global stack,
3. "retaddr <-- label" is done by pushing "label" onto (the same, multi-use) global stack (often part of CALL opcode, BALR opcode on early IBM360)
2. "send data to proc" is done via a global register (e.g. SP, BP, etc.)
4. GOTO is performed by CALL opcode (or BALR opcode)
5. Label is calculated dynamically (often using global PC register)