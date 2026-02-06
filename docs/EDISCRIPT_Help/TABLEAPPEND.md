EDI Script - (c) EDICOM s.r.o.

# TABLEAPPEND

appends a new record in a database table. The value can be set by a preceding instruction
        TABLEWRITE. The flag is set on if an error happens.

### Format:

## TABLEAPPEND ^a

a table pointer number

### Example:

TABLEOPEN ^0 "table.dbf"

        IF F THEN erropen

        LET $0="0123456789012"

        LET $1="Firm B"

        TABLEWRITE ^0 1 $0

        TABLEWRITE ^0 2 $1

        TABLEAPPEND ^0

        TABLECLOSE ^0

        END

        LABEL erropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLEWRITE](TABLEWRITE.md)

[TABLEUPDATE](TABLEUPDATE.md)
