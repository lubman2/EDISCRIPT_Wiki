EDI Script - (c) EDICOM s.r.o.

# EDIEXPORT

exports an EDIFACT message in ASCII or database file. Description of how to export
        is in a receipt file. This file can be created with Mapper.exe. If an export is
        not successful the flag is set on.

### Format:

## EDIEXPORT @a r [p]

a EDIFACT file pointer number (0 or 1) r string, register or constant with receipt file name p path for exported data files, the item is not mandatory

### Example:

EDIREAD @0 "test.edi" 1

        EDIEXPORT @0 "ordersex.rcp"

        IF F THEN err

        END

        LABEL err

        EDIERROR @0 $7

        ERROR $7

### See also:

[EDIREAD](EDIREAD.md)

[EDIIMPORT](EDIIMPORT.md)

[EDIWRITE](EDIWRITE.md)
