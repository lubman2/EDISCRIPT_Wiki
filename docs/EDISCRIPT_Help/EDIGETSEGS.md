EDI Script - (c) EDICOM s.r.o.

# EDIGETSEGS

retrieves number of segments in file opened by function EDIREAD. The flag is on
        set if error happens.

### Format:

## EDIGETSEGS @a #r

a EDIFACT file pointer number (0 or 1) r numeric register number

### Example:

EDIREAD @0 "test.edi" 1

        EDIGETSEGS @0 #1

### See also:

[EDIREAD](EDIREAD.md)

[EDIGERSEG](EDIGERSEG.md)

[EDICOUNT](EDICOUNT.md)
