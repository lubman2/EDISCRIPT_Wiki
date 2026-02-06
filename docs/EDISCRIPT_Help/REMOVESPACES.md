EDI Script - (c) EDICOM s.r.o.

# REMOVESPACES

removes redundant spaces in string register..

### Format:

## REMOVESPACES $a x

a number of string register with text x 0 = removes all spaces; 1 = leave maximum one space

### Example:

LET $0="Hallo world"

        REMOVESPACES $0 1 ; "Hallo world"

        LET $1="012 345 6789"

        REMOVESPACES $1 0 ; "0123456789"

### See also:

[STRCOPY](STRCOPY.md)

[TRIM](TRIM.md)

[STRUPPER](STRUPPER.md)

[NUMBER](NUMBER.md)
