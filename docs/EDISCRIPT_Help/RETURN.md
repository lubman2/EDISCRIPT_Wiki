EDI Script - (c) EDICOM s.r.o.

# RETURN

is a keyword which terminates the procedure. The procedure is a part of the program
        which can be used more then once in different parts of source file and in different
        actions.

### Format:

## RETURN

no parameters

### Example:

CALL myproc

        ...

        END

        PROC myproc

        ...

        RETURN

### See also:

[CALL](CALL.md)

[PROC](PROC.md)
