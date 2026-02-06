EDI Script - (c) EDICOM s.r.o.

# X12GET

gets one item from ANSI X12 message and puts this value in variable. The flag is
        on set if error happens.

### Format:

## X12GET @a r e

a ANSI X12 file pointer number (0 or 1) r string, numeric or floating point variable e EDI navigation

### Example:

X12READ @0 "test.X12" 1

        X12GET @0 $6 "UNH,2,1"

        X12GET @0 #5 "UNB,7,1"

### See also:

[X12SET](X12SET.md)

[X12READ](X12READ.md)

[X12COUNT](X12COUNT.md)
