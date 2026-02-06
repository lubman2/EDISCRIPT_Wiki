EDI Script - (c) EDICOM s.r.o.

# CERTLASTDATEEX

retrieves last valid date of certificate file. Password must be defined if private key is defined.
	The flag is set on if an error happens.

### Format:

## CERTLASTDATEEX #a f p

a numeric variable for time f file name for public or private key p password if private key is defined or empty string

### Example:

CERTLASTDATEEX #0 "C:\Certif\test.cer" ""

        IF !F THEN Ok

        LASTERROR @0 $0

        ...

        LABEL Ok

	TIMETOSTR #0 $1 0.

	BOX $1 "Test" 4

        CERTLASTDATEEX #0 "C:\Certif\test.pfx" "password"

        IF !F THEN Ok2

        LASTERROR @0 $0

        ...

        LABEL Ok2

	TIMETOSTR #0 $1 0.

	BOX $1 "Test" 4

        ...

### See also:

[CERTLASTDATE](CERTLASTDATE.md)

[EDISIGNEX](EDISIGNEX.md)
