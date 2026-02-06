EDI Script - (c) EDICOM s.r.o.

# SQLSELECT

executes SQL command SELECT. SQLFETCH then reads one line of result. SQLGET reads
        one value from the line.

### Format:

## SQLSELECT i n s

i instance of command (0, 1, 2) n number of columns in returned table s string with SQL command SELECT

### Example:

SQLCONNECT "DSN=edi"

        IF !F THEN Exec

        END

        LABEL Exec

        SQLSELECT 0 2 "SELECT NAME1,NAME2 FROM Names"

        IF !F THEN Fetch

        SQLERROR 0 $0

        END

        LABEL Fetch

        SQLFETCH 0

        IF F THEN close

        SQLGET 0 0 $3

        SQLGET 0 1 $4

        GOTO Fetch

        LABEL Close

        SQLCLOSE

### See also:

[SQLCONNECT](SQLCONNECT.md)

[SQLCLOSE](SQLCLOSE.md)

[SQLERROR](SQLERROR.md)

[SQLEXEC](SQLEXEC.md)
