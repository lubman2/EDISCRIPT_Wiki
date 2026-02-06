EDI Script - (c) EDICOM s.r.o.

# CERTLASTDATE

retrieves last valid date of the certificate. The certificate must be instaled in Window system.
	Password must be defined if private key is defined.
	The flag is set on if an error happens.

### Format:

## CERTLASTDATE #a f

a numeric variable for time f file name for public or private key

### Example:

CERTLASTDATE #0 "0011AA"

        IF !F THEN Ok

        LASTERROR @0 $0

        ...

        LABEL Ok

	TIMETOSTR #0 $1 0.

	BOX $1 "Test" 4

        ...

### See also:

[CERTLASTDATEEX](CERTLASTDATEEX.md)

[EDISIGNEX](EDISIGN.md)
