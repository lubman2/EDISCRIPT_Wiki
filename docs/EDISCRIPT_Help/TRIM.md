EDI Script - (c) EDICOM s.r.o.

# TRIM

removes leading and ending empty characters.

### Format:

## TRIM r

r string register

### Example:

LET $0=" abc "

        TRIM $0 ; result: "abc"

### See also:

[STRCOPY](STRCOPY.md)

[STRLEN](STRLEN.md)

[STRUPPER](STRUPPER.md)

[NUMBER](NUMBER.md)
