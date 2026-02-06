EDI Script - (c) EDICOM s.r.o.

# SQLSET

sets a value in SQL variable. The variables replace character % in command SQLEXEC.

### Format:

## SQLSET i n r

i instance of command (0, 1, 2) n variable number r string to put in variable

### Example:

SQLCONNECT "DSN=edi"

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

[SQLERROR](SQLERROR.md)

[SQLEXEC](SQLEXEC.md)
