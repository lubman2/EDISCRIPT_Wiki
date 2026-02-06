EDI Script - (c) EDICOM s.r.o.

# EDIDECIPHER

deciphers an EDIFACT message CIPHER to a file. The flag is set on if an error happens.
        The private key of certificate used in CIPHER message must be instaled in Window
        system.

### Format:

## EDIDECIPHER @a f

a EDIFACT file pointer number (0 or 1) for message to be deciphered f string or string variable with file name for a deciphered message to be saved

### Example:

EDIREAD @0 "test.edi" 0

        EDIDECIPHER @0 "file.edi"

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIDECIPHEREX](EDIDECIPHEREX.md)

[EDIREAD](EDIREAD.md)

[EDICIPHER](EDICIPHER.md)

[EDISIGN](EDISIGN.md)

[EDIVERIF](EDIVERIF.md)

[EDIAUTACK](EDIAUTACK.md)
