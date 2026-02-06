EDI Script - (c) EDICOM s.r.o.

# EDIVERIF

verifies a signature in the EDIFACT message. The flag is set on if an error happens.
        The public key for the signature used in message must be instaled in Window system.

### Format:

## EDIVERIF @a $n

a EDIFACT file pointer number (0 or 1) n number of string variable for hash from the signature

### Example:

EDIREAD @0 "test.edi" 0

        EDIVERIF @0 $L

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIVERIFEX](EDIVERIFEX.md)

[EDIREAD](EDIREAD.md)

[EDICIPHER](EDICIPHER.md)

[EDIDECIPHER](EDIDECIPHER.md)

[EDISIGN](EDISIGN.md)

[EDIAUTACK](EDIAUTACK.md)
