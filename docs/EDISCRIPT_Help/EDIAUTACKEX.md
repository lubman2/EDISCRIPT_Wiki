EDI Script - (c) EDICOM s.r.o.

# EDIAUTACKEX

creates an EDIFACT message AUTACK for the message opened in second EDIFACT pointer.
        The flag is set on if an error happens. The public key for verification must be in file defined in cer variable.
	The private key for the signature must be defined in pfx variable and password in pw variable.

### Format:

## EDIAUTACKEX @a @b cer pfx pw [h]

a EDIFACT file pointer number (0 or 1) for message to be verified b EDIFACT file pointer number (0 or 1) for the result message AUTACK cer string or string variable with file name of public certifikate for verification (*.cer) pfx string or string variable with file name of private key for singning message AUTACK (*.pfx) pw string or string variable with password for private key h hash algorithm: MD5, SHA1, SHA2; optional parameter

### Example:

EDIREAD @0 "test.edi" 0

        EDIAUTACKEX @0 @1 "firmA.cer" "my.pfx" "password" "SHA2"

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIAUTACK](EDIAUTACK.md)

[EDIREAD](EDIREAD.md)

[EDISIGNEX](EDISIGNEX.md)

[EDIVERIFEX](EDIVERIFEX.md)

[EDICIPHEREX](EDICIPHEREX.md)

[EDIDECIPHEREX](EDIDECIPHEREX.md)
