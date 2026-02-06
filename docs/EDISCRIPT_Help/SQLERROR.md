EDI Script - (c) EDICOM s.r.o.

# SQLERROR

returns error string after wrong SQL command.

### Format:

## SQLERROR i r

i instance of command (0, 1, 2) r string register for error text

### Example:

SQLCONNECT "DRIVER=SQL Server;SERVER=TEST;WSID=TEST;Database=MY_DATA"

        IF !F THEN Exec

        END

        LABEL Exec

        ...

        SQLSET 0 0 "Bill"

        SQLSET 0 1 "Gates"

        SQLEXEC 0 2 "INSERT INTO Names(Name1,Name2) VALUES('%','%')" $4

        IF !F THEN Close

        SQLERROR 0 $0

        ...

        LABEL Close

        SQLCLOSE

### See also:

[SQLCONNECT](SQLCONNECT.md)

[SQLCLOSE](SQLCLOSE.md)

[SQLSET](SQLSET.md)

[SQLEXEC](SQLEXEC.md)
