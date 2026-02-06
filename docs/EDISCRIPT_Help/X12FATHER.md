EDI Script - (c) EDICOM s.r.o.

# X12FATHER

sets the father of segment. This instruction is important for instructions X12SET
        and X12GET. If the segment is nested, the X12FATHER instruction must be used to
        set fathers of needed segments. Flag is set on if error happens.

### Format:

## X12FATHER @a e

a ANSI X12 file pointer number (0 or 1) e EDI navigation

### Example:

X12READ @0 "test.X12" 0

        X12FATHER @0 "LIN,1,1"

        X12GET @0 $3 "QTY,1,2,,1,0,1,1,21"

### See also:

[X12GET](X12GET.md)

[X12SET](X12SET.md)

[X12READ](X12READ.md)
