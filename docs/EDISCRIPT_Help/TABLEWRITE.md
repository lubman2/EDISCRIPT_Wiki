EDI Script - (c) EDICOM s.r.o.

# TABLEWRITE

writes one field in record of a database table. The record is saved in a file with
        the keywords TABLEUPDATE or TABLEAPPEND. The flag is set on if an error happens.

### Format:

## TABLEWRITE ^a f t

a table pointer number f field number, first field = 1 t text to save in field

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

[TABLEAPPEND](TABLEAPPEND.md)

[TABLEUPDATE](TABLEUPDATE.md)
