EDI Script - (c) EDICOM s.r.o.

# EDICIPHEREX

ciphers an EDIFACT message to the message CIPHER using public certificate of partner.
	The flag is set on if an error happens.

### Format:

## EDICIPHEREX @a @b cer

a EDIFACT file pointer number (0 or 1) for message to be ciphered b EDIFACT file pointer number (0 or 1) for the result message CIPHER cer string or string variable with file name of public certificate (*.cer)

### Example:

EDIREAD @0 "test.edi" 0

        EDICIPHEREX @0 @1 "firmA.cer"

        IF !F THEN Save

        EDIERROR @0 $0

        ...

        LABEL Save

        EDIWRITE @1 "cipher.edi" 0

        ...

### See also:

[EDICIPHER](EDICIPHER.md)

[EDIREAD](EDIREAD.md)

[EDIDECIPHEREX](EDIDECIPHEREX.md)

[EDISIGNEX](EDISIGNEX.md)

[EDIVERIFEX](EDIVERIFEX.md)

[EDIAUTACKEX](EDIAUTACKEX.md)
