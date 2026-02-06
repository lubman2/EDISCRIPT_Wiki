EDI Script - (c) EDICOM s.r.o.

# EDIVERIFEX

verifies a signature in the EDIFACT message. The flag is set on if an error happens.
        File name of the public key for the signature must be defined.
	If file name is empty default certifikate name is used: \Certif\(UNB,2,1)_(USC,1,1).cer (sender_serNum.cer).

### Format:

## EDIVERIFEX @a f $n

a EDIFACT file pointer number (0 or 1) f file name for public key, if string is empty default file name is used. n number of string variable for hash from the signature

### Example:

EDIREAD @0 "test.edi" 0

        EDIVERIFEX @0 "C:\Certif\test.cer" $L

        IF !F THEN Ok

        EDIERROR @0 $0

        ...

        LABEL Ok

        ...

### See also:

[EDIVERIF](EDIVERIF.md)

[EDIREAD](EDIREAD.md)

[EDICIPHEREX](EDICIPHEREX.md)

[EDIDECIPHEREX](EDIDECIPHEREX.md)

[EDISIGNEX](EDISIGNEX.md)

[EDIAUTACKEX](EDIAUTACKEX.md)
