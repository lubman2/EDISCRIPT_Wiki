EDI Script - (c) EDICOM s.r.o.

# TABLENEXT

searches for the next value of a specified string in a database table. The first
        value can be found with an instruction TABLEFIND. The flag is set on if the value
        is not found.

### Format:

## TABLENEXT ^a

a table pointer number

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

[TABLEFIND](TABLEFIND.md)
