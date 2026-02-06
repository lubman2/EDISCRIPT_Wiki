EDI Script - (c) EDICOM s.r.o.

# EDIGET

gets one item from EDIFACT message and puts this value in variable. The flag is
        on set if error happens.

### Format:

## EDIGET @a r e

a EDIFACT file pointer number (0 or 1) r string, numeric or floating point variable e EDIFACT navigation

### Example:

EDIREAD @0 "test.edi" 1

        EDIGET @0 $6 "UNH,2,1"

        EDIGET @0 #5 "UNB,7,1"

### See also:

[EDISET](EDISET.md)

[EDIREAD](EDIREAD.md)

[EDICOUNT](EDICOUNT.md)
