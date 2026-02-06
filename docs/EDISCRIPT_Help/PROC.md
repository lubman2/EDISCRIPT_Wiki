EDI Script - (c) EDICOM s.r.o.

# PROC

is a starting keyword for a procedure. The procedure is a part of a program which
        can be used more then once in different parts of source file and in different actions.
        The procedure must terminate with a keyword RETURN. It is not possible to call other
        procedures inside that procedure.

### Format:

## PROC p

p name of procedure

### Example:

CALL myproc

        ...

        END

        PROC myproc

        ...

        RETURN

### See also:

[CALL](CALL.md)

[RETURN](RETURN.md)
