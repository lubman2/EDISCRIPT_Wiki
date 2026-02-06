EDI Script - (c) EDICOM s.r.o.

# EDIERROR

copies the last error text in string variable.

### Format:

## EDIERROR @a $b

a EDIFACT file pointer number (0 or 1) b string variable number

### Example:

EDIEXPORT @0 $2

        IF !F THEN Label1

        EDIERROR @0 $1

        ERROR $1

### See also:

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)

[EDICOUNT](EDICOUNT.md)

[EDIMESSAGE](EDIMESSAGE.md)
