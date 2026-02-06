EDI Script - (c) EDICOM s.r.o.

# TABLEDELETE

deletes a record. The instruction The records for deleting can be selected by instructions
        TABLERECORD, TABLEFIND or TABLENEXT. The flag is set on if an error happens.

### Format:

## TABLEDELETE ^a

a table pointer number

### Example:

TABLEOPEN ^0 "table.dbf"

        IF F THEN erroropen

        LET #1=88

        TABLERECORD ^0 #1

        TABLEDELETE ^0

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)
