EDI Script - (c) EDICOM s.r.o.

# EDIUNBMSG

sets the pointer to the message with a specified UNB segment. The number of UNB
        segment is in a numeric register. The flag is set on if an error happens.

### Format:

## EDIUNBMSG @a b

a EDIFACT file pointer number (0 or 1) b numeric register or number, (0, 1, 2, ...)

### Example:

EDIREAD @0 "test.edi" 0

        IF F THEN Error

        LET #0=0

        LABEL Loop

        EDIUNBMSG @0 1 ; add UNB segment

        IF F THEN End

        EDIWRITE @0 "x.edi" 132

        IF F THEN Error

        LET #0=#0+1

        GOTO Loop

        LABEL Error

        EDIERROR @0 $0

        BOX $0 "EDI" 1

        LABEL End

        END

### See also:

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)
