EDI Script - (c) EDICOM s.r.o.

# X12RESET

resets all variables and memories linked with ANSI X12 file pointer (@). The flag
        is set to FALSE. All right reserved

### Format:

## X12RESET @a

a ANSI X12 file pointer number (0 or 1)

### Example:

X12READ @0 "test.X12" 1

        ...

        X12RESET @0

### See also:

[X12READ](X12READ.md)

[X12COUNT](X12COUNT.md)
