EDI Script - (c) EDICOM s.r.o.

# TABLEOPENXR

opens a database table for reading only. The instruction does not use index file.
        The table must be closed in the end with an instruction TABLECLOSE. The flag is
        set on if it is not possible to open the table.

### Format:

## TABLEOPENXR ^a n

a database pointer number, (0..2) d database file name, there is usually .DBF extension

### Example:

TABLEOPENXR ^0 "table.dbf"

        IF F THEN erroropen

        ...

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLECLOSE](TABLECLOSE.md)

[TABLEOPENX](TABLEOPENX.md)
