EDI Script - (c) EDICOM s.r.o.

# TABLECLOSE

closes a database. The flag is set on if the table is not possible to close.

### Format:

## TABLECLOSE ^a

a table pointer number

### Example:

TABLEOPEN ^0 "table.dbf"

        IF F THEN erroropen

        ...

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLECREATE](TABLECREATE.md)
