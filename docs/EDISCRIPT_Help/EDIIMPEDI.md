EDI Script - (c) EDICOM s.r.o.

# EDIIMPEDI

imports data from one EDIFACT message to other EDIFACT message. Description how
        to import data is in receipt file. This file can be created with program edircpt.exe.
        The flag is set on if error happens.

### Format:

## EDIIMPEDI @a @b r

a destination EDIFACT file pointer number (0 or 1) b source EDIFACT file pointer number (0 or 1) r string, string variable or constant with receipt file name

### Example:

EDIREAD @0 "test.edi" 1

        EDIIMPEDI @1 @0 "conv.rcp

        EDIWRITE @1 "newfile.edi" 2

### See also:

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)

[EDIIMPORT](EDIIMPORT.md)

[EDIEXPORT](EDIEXPORT.md)
