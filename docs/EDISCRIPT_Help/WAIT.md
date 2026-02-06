EDI Script - (c) EDICOM s.r.o.

# WAIT

interrupts a instruction sequence for specified milliseconds.

### Format:

## WAIT s

s numeric register or number of milliseconds to wait

### Example:

ACTION 1; My action

        ...

        WAIT 5000 ; wait 5 second

        ...

        END

### See also:

[ACTION](ACTION.md)

[END](END.md)

[ERROR](ERROR.md)
