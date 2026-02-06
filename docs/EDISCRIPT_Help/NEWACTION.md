EDI Script - (c) EDICOM s.r.o.

# NEWACTION

jumps to other ACTION and script continues there.

### Format:

## NEWACTION a

a new action number (0...255)

### Example:

ACTION 1 ; My action

        ...

        NEWACTION 2
        ;this code will never be run

        END

        ACTION 2

        ; script continues here"

        END

### See also:

[ACTION](ACTION.md)

[END](END.md)

[ERROR](ERROR.md)
