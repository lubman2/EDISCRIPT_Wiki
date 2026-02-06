EDI Script - (c) EDICOM s.r.o.

# TABLEFIND

searches for specified string in a database table. The next value can be found with
        an instruction TABLENEXT. The flag is set on if the value is not found.

### Format:

## TABLEFIND ^a s

a table pointer number s string to search

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

[TABLENEXT](TABLENEXT.md)
