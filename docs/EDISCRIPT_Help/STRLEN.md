EDI Script - (c) EDICOM s.r.o.

# STRLEN

calculates length of string and returns it in numeric register.

### Format:

## STRLEN #a $b

a number of numeric register for length of string b string to calculate length

### Example:

LET $1="0123456789"

        STRLEN #0 $1 ; #0 = 10

### See also:

[STRCOPY](STRCOPY.md)
