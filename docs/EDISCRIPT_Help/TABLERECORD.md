EDI Script - (c) EDICOM s.r.o.

# TABLERECORD

sets the file pointer to a selected record. The flag is set on if an error happens.

### Format:

## TABLERECORD ^a #b

a table pointer number b numeric variable number with record number, record number starts from 1 r string

### Example:

TABLEOPEN ^0 "table.dbf"

        IF F THEN erroropen

        LET $0="8590123456789"

        LET $1="Firm A"

        LET #1=5

        TABLERECORD ^0 #1

        TABLEWRITE ^0 1 $0

        TABLEWRITE ^0 2 $1

        TABLEUPDATE ^0

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLEREAD](TABLEREAD.md)

[TABLEWRITE](TABLEWRITE.md)
