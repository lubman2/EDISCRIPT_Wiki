EDI Script - (c) EDICOM s.r.o.

# X12COUNT

calculates number of messages in loaded ANSI X12 file and saves this value in numeric
        register. Instruction sets the flag if error happens.

### Format:

## X12COUNT @a #b

a ANSI X12 file pointer number (0 or 1) b numeric register number

### Example:

X12READ @0 "test.X12" 0

        X12COUNT @0 #5

### See also:

[X12READ](X12READ.md)

[X12MESSAGE](X12MESSAGE.md)
