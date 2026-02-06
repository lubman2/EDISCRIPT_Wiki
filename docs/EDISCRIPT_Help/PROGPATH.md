EDI Script - (c) EDICOM s.r.o.

# PROGPATH

copies a full directory of the program to a string variable.

### Format:

## PROGPATH $a

a string variable number

### Example:

PROGPATH $8

        LET $9=$8+"edi.ini"

### See also:

[RUN](RUN.md)

[INIREAD](INIREAD.md)

[INIWRITE](INIWRITE.md)
