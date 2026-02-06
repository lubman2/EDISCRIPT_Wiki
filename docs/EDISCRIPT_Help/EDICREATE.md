EDI Script - (c) EDICOM s.r.o.

# EDICREATE

creates new EDIFACT file.

### Format:

## EDICREATE @a type release flag

a EDIFACT file pointer number (0 or 1) type 6 characters for type of message release 3 characters for release flag 4 for UNB segment, 6 for UNA and UNB segment

### Example:

EDICREATE @0 "ORDERS" "93A" 6

### See also:

[EDIREAD](EDIREAD.md)

[EDIWRITE](EDIWRITE.md)
