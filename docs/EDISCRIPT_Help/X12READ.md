EDI Script - (c) EDICOM s.r.o.

# X12READ

loads an ANSI X12 file in memory and sets a pointer to the first message in file.
        The flag is set on if an error happens.

### Format:

## X12READ @a n r

a ANSI X12 file pointer number (0 or 1) n string, string variable or constant with file name to read r 0 = full access; bit 1 = read only; bit 2 = do not go on first message; bit 4 = do not change date and time in UNB segment

### Example:

X12READ @0 "test.X12" 0

        IF !F THEN Label1

        X12ERROR @0 $1

        ERROR $1

        END

        LABEL Label1

        ...

### See also:

[X12WRITE](X12WRITE.md)

[X12COUNT](X12COUNT.md)
