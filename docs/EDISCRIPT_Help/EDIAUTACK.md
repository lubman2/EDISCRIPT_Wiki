EDI Script - (c) EDICOM s.r.o.

# EDIAUTACK

creates an EDIFACT message AUTACK for the message opened in second EDIFACT pointer.
        The flag is set on if an error happens.The private key for the signature must be
        instaled in Window system.

### Format:

## EDIAUTACK @a @b key [h]

a EDIFACT file pointer number (0 or 1) for message to be verified b EDIFACT file pointer number (0 or 1) for the result message AUTACK key string or string variable with serial number of private key (hexadecimal number
                without spaces) h hash algorithm: MD5, SHA1, SHA2; optional parameter

### Example:

EDIREAD @0 "test.edi" 0

        EDIAUTACK @0 @1 "012b6a" "SHA2"

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIAUTACKEX](EDIAUTACKEX.md)

[EDIREAD](EDIREAD.md)

[EDISIGN](EDISIGN.md)

[EDIVERIF](EDIVERIF.md)

[EDICIPHER](EDICIPHER.md)

[EDIDECIPHER](EDIDECIPHER.md)
