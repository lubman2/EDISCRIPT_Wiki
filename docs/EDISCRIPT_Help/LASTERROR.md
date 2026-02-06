EDI Script - (c) EDICOM s.r.o.

# LASTERROR

copies the last error text in string variable.

### Format:

## LASTERROR $b

b string variable number

### Example:

EDIEXPORT @0 $2

        IF !F THEN Label1

        LASTERROR $1

        ERROR $1

### See also:

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)

[EDICOUNT](EDICOUNT.md)

[EDIMESSAGE](EDIMESSAGE.md)
