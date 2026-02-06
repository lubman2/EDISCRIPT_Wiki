EDI Script - (c) EDICOM s.r.o.

# X12SET

saves one item in ANSI X12 message. This value is in variable. The flag is set on
        if an error happens.

### Format:

## X12SET @a r e

a ANSI X12 file pointer number (0 or 1) r string, numeric or floating point variable e EDI navigation

### Example:

X12READ @0 "test.X12" 0

        LET $6="1"

        LET #5=126

        X12SET @0 $6 "UNB,7,1"

        X12SET @0 #5 "BGM,1,1"

### See also:

[X12GET](X12GET.md)

[X12READ](X12READ.md)

[X12COUNT](X12COUNT.md)
