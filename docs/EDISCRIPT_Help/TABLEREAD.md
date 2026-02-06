EDI Script - (c) EDICOM s.r.o.

# TABLEREAD

reads one field from a record. The record is selected after the instruction TABLERECORD,
        TABLEFIND or TABLENEXT. The flag is set on if an error happens.

### Format:

## TABLEREAD ^a f v

a table pointer number f field number, first field = 1 v variable for read value

### Example:

TABLEOPEN ^0 "table.dbf"

        IF F THEN erroropen

        TABLEFIND ^0 "8590123456789"

        LABEL search

        IF F THEN endsearch

        TABLEREAD ^0 2 $2

        ...

        TABLENEXT ^0

        GOTO search

        LABEL endsearch

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLERECORD](TABLERECORD.md)

[TABLEFIND](TABLEFIND.md)

[TABLENEXT](TABLENEXT.md)
