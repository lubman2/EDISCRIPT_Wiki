EDI Script - (c) EDICOM s.r.o.

# EDISIGNEX

adds signature in an EDIFACT message. The flag is set on if an error happens. The
        private key for the signature must be in pfx file.
	There are 2 versions of syntax. Long version is for default signature. Short version is for more possibilities
        to set signature. If "USH,1,1" is set to 1, then Spar signature is required. If
        "USH,5,1" is set to 2, AUTACK is required. It is also possible to set hash algorithm
        in item "USA,1,4,,1": 6 is MD5; 16 is SHA1; 48 is SHA2. If item "USA,1,1,,1" is
        set, program assume all items has been set and program does not set any default items.

### Format:

## EDISIGNEX @e pfx pw $n [h a]

e EDIFACT file pointer number (0 or 1) pfx string or string variable with file with certificate (*.pfx) pw string or string variable with password for private key n number of string variable for hash created by this function h optional, hash algorithm: MD5, SHA1, SHA2 a optional, request of AUTACK message: 1 - AUTACK not requested 2 - AUTACK requested

### Example:

EDIREAD @0 "test.edi" 0

        EDISIGNEX @0 "my.pfx" "password" $L "SHA2" 2

        IF !F THEN Save

        EDIERROR @0 $0

        END

        LABEL Save

        EDIWRITE @0 "testSigned.edi" 0

        END

        ...

        EDIREAD @0 "test.edi" 0

        EDISET @0 "2" "USH,5,1" ; AUTACK requested

        EDISET @0 "48" "USA,1,1,,1" ; SHA2

        EDISIGNEX @0 "my.pfx" "password" $L

        IF !F THEN Save

        EDIERROR @0 $0

        END

        LABEL Save

        EDIWRITE @0 "testSigned.edi" 0

        END

        ...

        EDIREAD @0 "test.edi" 0

        EDISET @0 "1" "USH,1,1" ; required Spar signature

        EDISIGNEX @0 "my.pfx" "password" $L

        IF !F THEN Save

        EDIERROR @0 $0

        END

        LABEL Save

        EDIWRITE @0 "testSigned.edi" 0

        END

### See also:

[EDISIGN](EDISIGN.md)

[EDIREAD](EDIREAD.md)

[EDIVERIFEX](EDIVERIFEX.md)

[EDICIPHEREX](EDICIPHEREX.md)

[EDIDECIPHEREX](EDIDECIPHEREX.md)

[EDIAUTACKEX](EDIAUTACKEX.md)
