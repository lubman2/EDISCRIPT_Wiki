EDI Script - (c) EDICOM s.r.o.

# EDIUNB

adds or removes UNB and UNZ segment. The function creates communication envelope.
        The function adds UNB segment before first message and UNZ segment after last message.
        The flag is set on if an error happens.

### Format:

## EDIUNB @a x

a EDIFACT file pointer number (0 or 1) x 0 for segment to remove; 1 for segment to add

### Example:

EDIREAD @0 "test.edi" 0

        IF F THEN Error

        EDIUNB @0 1 ; add UNB segment

        IF F THEN Error

        EDIWRITE @0 "test.edi" 1

        IF F THEN Error

        END

        LABEL Error

        EDIERROR @0 $0

        BOX $0 "EDI" 1

        END

### See also:

[EDIUNA](EDIUNA.md)

[EDIGET](EDIGET.md)

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)
