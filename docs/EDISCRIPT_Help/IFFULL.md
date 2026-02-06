EDI Script - (c) EDICOM s.r.o.

# IFFULL

tests, if the string variable is not empty. If the string variable is not empty
        the program jumps to the LABEL which has the same name like the name after THEN.
        If the string variable is empty the program continues on the next line.

### Format:

## IFFULL $a THEN b

a string variable number (0..9,L) b name of label to jump if string variable is not empty

### Example:

IFFULL $0 THEN a1

        ...

        LABEL a1

        ...

### See also:

[IFEMPTY](IFEMPTY.md)

[IF](IF.md)
