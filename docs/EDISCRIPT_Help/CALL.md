EDI Script - (c) EDICOM s.r.o.

# CALL

is a keyword for calling procedure. The procedure is part of a program which can
        be used more then once in different parts of source file and in different actions.
        It is not possible to use CALL inside procedure.

### Format:

## CALL procname

procname name of procedure

### Example:

CALL myproc

        ...

        END

        PROC myproc

        ...

        RETURN

### See also:

[PROC](PROC.md)

[RETURN](RETURN.md)
