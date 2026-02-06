EDI Script - (c) EDICOM s.r.o.

# TABLECREATE

creates a new database table. The database is always indexed by the first field.
        The search is working for first field only. The flag is set on if the table was
        not created.

### Format:

## TABLECREATE n f,t,n,d [f,t,n,d ...]

n name of table, extension should be .DBF f field name, max. 10 characters t type, C = character, N = numeric, L logical, D date, M = memo n length of field d decimal value, digits after floating point, for numeric type only, for other types
                d = 0

### Example:

TABLECREATE "table.dbf" "EAN",C,13,0 "FIRM",C,35,0

        IF F THEN errorcreate

        ...

        END

        LABEL errorcreate

        ERROR "Cannot create table"

### See also:

[TABLEOPEN](TABLEOPEN.md)

[TABLECLOSE](TABLECLOSE.md)
