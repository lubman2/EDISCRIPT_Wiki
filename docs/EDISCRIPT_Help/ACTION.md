EDI Script - (c) EDICOM s.r.o.

# ACTION

is a starting point for every process. The keyword ACTION is followed by number of
        process. Every process must finish with the keywords END or ERROR. There can be
        more then one ACTION in EDI script file.

### Format:

## ACTION a

a action number (0...255)

### Example:

ACTION 1 ; My action

        ...

        IF F THEN error

        ...

        END

        LABEL error

        ERROR "Error in action 1"

### See also:

[END](END.md)

[ERROR](ERROR.md)
