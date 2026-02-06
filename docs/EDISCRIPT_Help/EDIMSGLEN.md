EDI Script - (c) EDICOM s.r.o.

# EDIMSGLEN

returns number of characters of in selected message. The flag is set on if an error
        happens.

### Format:

## EDIMSGLEN @a #x

a EDIFACT file pointer number (0 or 1) x number variable

### Example:

EDIREAD @0 "test.edi" 100 150

        IF !F THEN Label1

        EDIMSGLEN @0 #0

        EDIERROR @0 $1

        ERROR $1

### See also:

[EDIWRITE](EDIWRITE.md)

[EDICOUNT](EDICOUNT.md)
