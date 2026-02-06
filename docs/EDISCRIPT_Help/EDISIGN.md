EDI Script - (c) EDICOM s.r.o.

# EDISIGN

adds signature in an EDIFACT message. The flag is set on if an error happens. The
        private key for the signature must be instaled in Window system.
	There are 2 versions of syntax. Long version is for default signature. Short version is for more possibilities
        to set signature. If "USH,1,1" is set to 1, then Spar signature is required. If
        "USH,5,1" is set to 2, AUTACK is required. It is also possible to set hash algorithm
        in item "USA,1,4,,1": 6 is MD5; 16 is SHA1; 48 is SHA2. If item "USA,1,1,,1" is
        set, program assume all items has been set and does not set any default items.

### Format:

## EDISIGN @e key $n [h a]

e EDIFACT file pointer number (0 or 1) key string or string variable with serial number of private key (hexadecimal number
                without spaces) n number of string variable for hash created by this function h optional, hash algorithm: MD5, SHA1, SHA2 a optional, request of AUTACK message: 1 - AUTACK not requested 2 - AUTACK requested

### Example:

EDIREAD @0 "test.edi" 0

        EDISIGN @0 "012b6a" $L "SHA2" 2

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

        EDISIGN @0 "012b6a" $L

        IF !F THEN Save

        EDIERROR @0 $0

        END

        LABEL Save

        EDIWRITE @0 "testSigned.edi" 0

        END

        ...

        EDIREAD @0 "test.edi" 0

        EDISET @0 "1" "USH,1,1" ; required Spar signature

        EDISIGN @0 "012b6a" $L

        IF !F THEN Save

        EDIERROR @0 $0

        END

        LABEL Save

        EDIWRITE @0 "testSigned.edi" 0

        END

### See also:

[EDISIGNEX](EDISIGNEX.md)

[EDIREAD](EDIREAD.md)

[EDIVERIF](EDIVERIF.md)

[EDICIPHER](EDICIPHER.md)

[EDIDECIPHER](EDIDECIPHER.md)

[EDIAUTACK](EDIAUTACK.md)
