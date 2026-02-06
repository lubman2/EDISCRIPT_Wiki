EDI Script - (c) EDICOM s.r.o.

# EDISET

saves one item in EDIFACT message. This value is in variable. The flag is set on
        if an error happens.

### Format:

## EDISET @a r e

a EDIFACT file pointer number (0 or 1) r string, numeric or floating point variable e EDIFACT navigation

### Example:

EDIREAD @0 "test.edi" 0

        LET $6="1"

        LET #5=126

        EDISET @0 $6 "UNB,7,1"

        EDISET @0 #5 "BGM,1,1"

### See also:

[EDIGET](EDIGET.md)

[EDIREAD](EDIREAD.md)

[EDICOUNT](EDICOUNT.md)
