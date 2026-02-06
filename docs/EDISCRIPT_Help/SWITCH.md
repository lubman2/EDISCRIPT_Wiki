EDI Script - (c) EDICOM s.r.o.

# SWITCH

allows the user to switch the program in different parts according to the string
        variable. The SWITCH is usually followed by the keyword CASE. If the text of the
        CASE is the same like the text in the variable, the program jumps to the label whose
        name is at the end of the CASE instruction. If the text in variable does not exist
        in any instruction CASE then the program continues on next line after the last CASE.

### Format:

## SWITCH $n

n string register number, $0..$9,$L

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

[CASE](CASE.md)

[LABEL](LABEL.md)
