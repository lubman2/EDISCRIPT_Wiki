EDI Script - (c) EDICOM s.r.o.

# EDIREADMSG

loads an EDIFACT file in memory and sets a pointer to the first message in file.
        The flag is set on if an error happens.

### Format:

## EDIREADMSG @a f p l

a EDIFACT file pointer number (0 or 1) f string, string variable or constant with file name to read p position in file n number of characters to read

### Example:

EDIREADMSG @0 "test.edi" 100 150

        IF !F THEN Label1

        EDIERROR @0 $1

        ERROR $1

### See also:

[EDIWRITE](EDIWRITE.md)

[EDICOUNT](EDICOUNT.md)
