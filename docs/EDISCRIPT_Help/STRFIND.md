EDI Script - (c) EDICOM s.r.o.

# STRFIND

finds string in text. The function returns position if string is found.
        If string is not found, the function returns -1 and set flag.

### Format:

## STRFIND t f #p

t text string f string to find p result: number of numeric register for position in text string, starts from 0

### Example:

LET $0="123;456;789"

        STRFIND $0 ";" #0 ; result: 3

### See also:

[STRFINDX](STRFINDX.md)

[LET](LET.md)

[STRCOPY](STRCOPY.md)

[STRLEN](STRLEN.md)
