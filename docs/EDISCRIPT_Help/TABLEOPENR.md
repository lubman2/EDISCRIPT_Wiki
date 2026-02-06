EDI Script - (c) EDICOM s.r.o.

# TABLEOPENR

opens a database table for reading only. The instruction creates index file if the
        file does not exist. The index file is created for first column. The table must
        be closed in the end with an instruction TABLECLOSE. The flag is set on if it is
        not possible to open the table.

### Format:

## TABLEOPENR ^a n

a database pointer number, (0..2) n database file name, there is usually .DBF extension

### Example:

TABLEOPENR ^0 "table.dbf"

        IF F THEN erroropen

        ...

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLECLOSE](TABLECLOSE.md)

[TABLEOPEN](TABLEOPEN.md)
