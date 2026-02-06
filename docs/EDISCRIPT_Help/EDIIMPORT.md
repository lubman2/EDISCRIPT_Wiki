EDI Script - (c) EDICOM s.r.o.

# EDIIMPORT

creates an EDIFACT message from any text or database file. Description of how to convert
        is in a receipt file. This file can be created with the program mapper.exe. The
        flag is set on if error happens.

### Format:

## EDIIMPORT @a r [p]

a EDIFACT file pointer number (0 or 1) r string, string variable or constant with receipt file name p path with data files, the item is not mandatory

### Example:

EDIIMPORT @0 "ordersim.rcp"

        IF !F THEN Write

        EDIERROR @0 $7

        ERROR $7

        LABEL Write

        EDIWRITE @0 "test.edi" 4

        IF !F THEN End

        ERROR "Cannot write in test.edi"

        LABEL End

        ...

### See also:

[EDIEXPORT](EDIEXPORT.md)

[EDIREAD](EDIREAD.md)

[EDICOUNT](EDICOUNT.md)
