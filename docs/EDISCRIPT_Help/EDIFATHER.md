EDI Script - (c) EDICOM s.r.o.

# EDIFATHER

sets the father of segment. This instruction is important for instructions EDISET
        and EDIGET. If the segment is nested, the EDIFATHER instruction must be used to
        set fathers of needed segments. Flag is set on if error happens.

### Format:

## EDIFATHER @a e

a EDIFACT file pointer number (0 or 1) e EDIFACT navigation

### Example:

EDIREAD @0 "test.edi" 0

        EDIFATHER @0 "LIN,1,1"

        EDIGET @0 $3 "QTY,1,2,,1,0,1,1,21"

### See also:

[EDIGET](EDIGET.md)

[EDISET](EDISET.md)

[EDIREAD](EDIREAD.md)
