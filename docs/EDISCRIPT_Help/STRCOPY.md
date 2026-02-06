EDI Script - (c) EDICOM s.r.o.

# STRCOPY

copies one string to the other one in a selected position and in a specified length.
        This instruction is important for formatted output strings.

### Format:

## STRCOPY d s p l f

d destination string s source string p position in destination string, starts from 0 l length of string to copy; if length is 0 whole string is copied f position in source string, starts from 0

### Example:

LET $0="01234567890123456789"

        LET $1="ABCDEF"

        STRCOPY $0 $1 4 6 0 ; result "0123ABCDEF0123456789"

        STRCOPY $3 $0 10 0 0 ; result "0123456789"

### See also:

[LET](LET.md)

[STRUPPER](STRUPPER.md)

[TRIM](TRIM.md)
