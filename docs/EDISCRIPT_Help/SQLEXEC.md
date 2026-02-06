EDI Script - (c) EDICOM s.r.o.

# SQLEXEC

executes an SQL command.

### Format:

## SQLEXEC i n c r

i instance of command (0, 1, 2) n number of variables c SQL command, character % are replaced with variables r string register for a result string

### Example:

SQLCONNECT "DSN=EDI"

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

[SQLERROR](SQLERROR.md)
