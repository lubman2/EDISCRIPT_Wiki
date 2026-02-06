EDI Script - (c) EDICOM s.r.o.

# EDIMESSAGE

sets the pointer to the message, which has the number in a numeric register. The
        flag is set on if an error happens.

### Format:

## EDIMESSAGE @a b

a EDIFACT file pointer number (0 or 1) b numeric register or number, (0, 1, 2, ...)

### Example:

EDIREAD @0 "test.edi" 1

        LET #0=0

        EDIMESSAGE @0 #0

### See also:

[EDICOUNT](EDICOUNT.md)

[EDIREAD](EDIREAD.md)
