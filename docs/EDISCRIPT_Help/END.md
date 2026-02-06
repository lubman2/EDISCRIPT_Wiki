EDI Script - (c) EDICOM s.r.o.

# END

terminates an action. The action starts with a keyword ACTION and must be terminated
        with an END or ERROR.

### Format:

## END

no parameters

### Example:

ACTION 1 ; My action

        ...

        IF F THEN error

        ...

        END

        LABEL error

        ...

        ERROR "Error in my action"

### See also:

[ACTION](ACTION.md)

[ERROR](ERROR.md)
