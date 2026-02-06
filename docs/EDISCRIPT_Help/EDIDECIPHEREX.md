EDI Script - (c) EDICOM s.r.o.

# EDIDECIPHEREX

deciphers an EDIFACT message CIPHER to a file. The flag is set on if an error happens.
        File name of the private key of certificate used in CIPHER message must be defined in pfx variable and password in pw variable.

### Format:

## EDIDECIPHEREX @a pfx pw f

a EDIFACT file pointer number (0 or 1) for message to be deciphered pfx string or string variable with file name of private key (*.pfx) pw string or string variable with password of private key f string or string variable with file name for a deciphered message to be saved

### Example:

EDIREAD @0 "test.edi" 0

        EDIDECIPHEREX @0 "my.pfx" "password" "file.edi"

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIDECIPHER](EDIDECIPHER.md)

[EDIREAD](EDIREAD.md)

[EDICIPHEREX](EDICIPHEREX.md)

[EDISIGNEX](EDISIGNEX.md)

[EDIVERIFEX](EDIVERIFEX.md)

[EDIAUTACKEX](EDIAUTACKEX.md)
