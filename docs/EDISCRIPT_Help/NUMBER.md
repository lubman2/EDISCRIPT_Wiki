EDI Script - (c) EDICOM s.r.o.

# NUMBER

correctes a number in a string register to valid number.

### Format:

## NUMBER r

r string register

### Example:

LET $0="1,234.50"

        NUMBER $0 ; result "1234.50"

### See also:

[STRCOPY](STRCOPY.md)

[STRLEN](STRLEN.md)

[STRUPPER](STRUPPER.md)

[TRIM](TRIM.md)
