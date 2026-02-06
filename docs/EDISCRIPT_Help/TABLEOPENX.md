EDI Script - (c) EDICOM s.r.o.

# TABLEOPENX

opens a database table. The instruction does not creates index file. The table must
        be closed in the end with an instruction TABLECLOSE. The flag is set on if it is
        not possible to open the table.

### Format:

## TABLEOPENX ^a n

a database pointer number, (0..2) n database file name, there is usually .DBF extension

### Example:

TABLEOPENX ^0 "table.dbf"

        IF F THEN erroropen

        ...

        TABLECLOSE ^0

        END

        LABEL erroropen

        ERROR "Cannot open table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLECLOSE](TABLECLOSE.md)

[TABLEFIND](TABLEFIND.md)

[TABLEAPPEND](TABLEAPPEND.md)
