EDI Script - (c) EDICOM s.r.o.

# EDICIPHER

ciphers an EDIFACT message to the message CIPHER using public certificate of partner. The flag is set on if an error
        happens.

### Format:

## EDICIPHER @a @b key

a EDIFACT file pointer number (0 or 1) for message to be ciphered b EDIFACT file pointer number (0 or 1) for the result message CIPHER key string or string variable with serial number of public certificate of partner (hexadecimal number
                without spaces)

### Example:

EDIREAD @0 "test.edi" 0

        EDICIPHER @0 @1 "012b6a"

        IF !F THEN Save

        EDIERROR @0 $0

        ...

        LABEL Save

        EDIWRITE @1 "cipher.edi" 0

        ...

### See also:

[EDICIPHEREX](EDICIPHEREX.md)

[EDIREAD](EDIREAD.md)

[EDIDECIPHER](EDIDECIPHER.md)

[EDISIGN](EDISIGN.md)

[EDIVERIF](EDIVERIF.md)

[EDIAUTACK](EDIAUTACK.md)
