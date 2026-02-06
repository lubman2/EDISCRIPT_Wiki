EDI Script - (c) EDICOM s.r.o.

# X12MESSAGE

sets the pointer to the message, which has the number in a numeric register. The
        flag is set on if an error happens.

### Format:

## X12MESSAGE @a b

a ANSI X12 file pointer number (0 or 1) b numeric register or number, (0, 1, 2, ...)

### Example:

X12READ @0 "test.X12" 1

        LET #0=0

        X12MESSAGE @0 #0

### See also:

[X12COUNT](X12COUNT.md)

[X12READ](X12READ.md)
