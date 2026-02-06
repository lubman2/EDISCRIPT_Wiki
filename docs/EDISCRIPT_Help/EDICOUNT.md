EDI Script - (c) EDICOM s.r.o.

# EDICOUNT

calculates number of messages in loaded EDIFACT file and saves this value in numeric
        register. Instruction sets the flag if error happens.

### Format:

## EDICOUNT @a #b

a EDIFACT file pointer number (0 or 1) b numeric register number

### Example:

EDIREAD @0 "test.edi" 0

        EDICOUNT @0 #5

### See also:

[EDIREAD](EDIREAD.md)

[EDIMESSAGE](EDIMESSAGE.md)
