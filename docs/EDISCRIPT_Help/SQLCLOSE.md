EDI Script - (c) EDICOM s.r.o.

# SQLCLOSE

closes the SQL connection opened by function SQLCONNECT.

### Format:

## SQLCLOSE

no parameters

### Example:

SQLCONNECT "DSN=EDI"

        IF !F THEN Exec

        END

        LABEL Exec

        ...

        SQLCLOSE

### See also:

[SQLCONNECT](SQLCONNECT.md)

[SQLSELECT](SQLSELECT.md)

[SQLEXEC](SQLEXEC.md)
