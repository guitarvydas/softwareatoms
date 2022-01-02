
alloc data
send data to proc
goto dest

In typical cases:
1. data is allocated (by value, sometimes by reference) in a global register
2. send is implicit (data remains in global register)
3. GOTO dest is performed by dynamically calculating "dest" (usually by accessing (SP)) then assigning dest to PC

i.e. Return is a dynamic GOTO
