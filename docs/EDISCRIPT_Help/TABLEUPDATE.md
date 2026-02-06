EDI Script - (c) EDICOM s.r.o.

# TABLEUPDATE

updates a record. The value in the record can be changed with a TABLEWRITE. The
        flag is set on if an error happens.

### Format:

## TABLEUPDATE ^a

a table pointer number

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

[TABLERECORD](TABLERECORD.md)

[TABLEWRITE](TABLEWRITE.md)
