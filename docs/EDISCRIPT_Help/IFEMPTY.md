EDI Script - (c) EDICOM s.r.o.

# IFEMPTY

tests, if string variable is empty. If string variable is empty the program jumps
        to a LABEL which has the same name like the name after THEN. If the string variable
        is not empty the program continues on the next line.

### Format:

## IFEMPTY $a THEN b

a string variable number (0..9,L) b name of label to jump if string variable is empty

### Example:

IFEMPTY $0 THEN a1

        ...

        LABEL a1

        ...

### See also:

[IFFULL](IFFULL.md)

[IF](IF.md)
