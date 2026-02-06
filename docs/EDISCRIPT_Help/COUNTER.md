EDI Script - (c) EDICOM s.r.o.

# COUNTER

retrieves a number from the specified counter and increments this counter. Counter
        value is saved in edi.ini file in section Counters. If value for specified counter
        is not present counter retrievs 0 and new value = 1 is saved in ini file.

### Format:

## COUNTER a b

a format of counter: name^Cx[^X^Y^M^D...] name is name of the counter x is number of digits in the counter value X is year with 4 characters Y is year with 2 characters M for month D of year it is possible to insert any other character it is possible to use E instead of C then number has fixed length with leading zeros b string register for the counter value

### Example:

COUNTER "Interchange^C6" $0 ; 1

        COUNTER "Interchange^E6" $0 ; 000001

        COUNTER "INVOICE^E6^/^Y" $1 ; 000008/99

        COUNTER "ORDERS^Y^M^E4" $2 ; 99120005

        COUNTER "Autack'AUTACK^C6" $2 ; AUTACK7

### See also:

[INIREAD](INIREAD.md)

[INIWRITE](INIWRITE.md)
