EDI Script - (c) EDICOM s.r.o.

# EDIREAD

loads an EDIFACT file in memory and sets a pointer to the first message in file.
        The flag is set on if an error happens.

### Format:

## EDIREAD @a n r

a EDIFACT file pointer number (0 or 1) n string, string variable or constant with file name to read r 0 = full access; bit 1(1) = read only; bit 2(2) = do not go on first message; bit 3(4) = do not change date and time in UNB segment bit 4(8) = read message without EMF file, works for 0 level only

### Example:

EDIREAD @0 "test.edi" 0

        IF !F THEN Label1

        EDIERROR @0 $1

        ERROR $1

        END

        LABEL Label1

        ...

### See also:

[EDIWRITE](EDIWRITE.md)

[EDICOUNT](EDICOUNT.md)
