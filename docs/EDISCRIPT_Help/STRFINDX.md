EDI Script - (c) EDICOM s.r.o.

# STRFINDX

finds repeated string in text. The function returns position if string is found.
        If string is not found, the function returns -1 and set flag.

### Format:

## STRFINDX t f #p r

t text string f string to find p result: number of numeric register for position in text string, starts from 0 r number of repeats, starts from 1

### Example:

LET $0="123;456;789"

        STRFINDX $0 ";" #0 2 ; result: 7

### See also:

[STRFIND](STRFIND.md)

[LET](LET.md)

[STRCOPY](STRCOPY.md)

[STRLEN](STRLEN.md)
