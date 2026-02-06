EDI Script - (c) EDICOM s.r.o.

# CASE

is placed after a keyword SWITCH. If the text followed by keyword CASE is the same
        like the text in string variable in instruction SWITCH, then the program jumps to
        keyword LABEL. The name of label is the second parameter of instruction CASE. If
        the text in variable does not exist in any instruction CASE then the program continues
        on next line after the last CASE.

### Format:

## CASE a b

a string or constant b name of label to jump if string is the same as the string in variable in instruction
                SWITCH

### Example:

CONST Inv "INVOIC"

        LET $1="ORDERS"

        SWITCH $1

        CASE "ORDERS" orders

        CASE Inv invoice

        ERROR "Type not known"

        LABEL orders

        ...

        END

        LABEL invoice

        ...

        END

### See also:

[SWITCH](SWITCH.md)

[LABEL](LABEL.md)
