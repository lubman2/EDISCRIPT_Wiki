EDI Script - (c) EDICOM s.r.o.

# Variables

EDI Script uses this variables:

$0 - $9 String with max. 255 characters $L Long string with max. 8191 characters #0 - #9 Numeric variable (-2,147,483,648 to 2,147,483,647) ~0 - ~2 Floating point variable (3.4 * (10**-38) to 3.4 * (10**+38)) @0, @1 EDIFACT pointer ^0 - ^2 Pointer to table, maximum 3 tables can be opened at the same time F Flag (some instruction set this flag according result of action)

### Example:

LET $5="My text"

        LET #4=999

        LET ~2=3.14

        EDIREAD @0 "test.edi" 1

        IF F THEN error

        ...

        LABEL error

        ...

        END
