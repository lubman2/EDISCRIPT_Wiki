EDI Script - (c) EDICOM s.r.o.

# EDIRESET

resets all variables and memories linked with EDIFACT file pointer (@). The flag
        is set to FALSE. All right reserved

### Format:

## EDIRESET @a

a EDIFACT file pointer number (0 or 1)

### Example:

EDIREAD @0 "test.edi" 1

        ...

        EDIRESET @0

### See also:

[EDIREAD](EDIREAD.md)

[EDICOUNT](EDICOUNT.md)
