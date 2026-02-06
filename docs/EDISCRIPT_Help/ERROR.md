EDI Script - (c) EDICOM s.r.o.

# ERROR

terminates an action with an error message. Every action must start with a keyword
        ACTION and terminates with the keyword END or ERROR.

### Format:

## ERROR a

a string or string register; action is terminated with this message, usually it is
                displayed in an error dialog window or it is written in a log file

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

[END](END.md)
