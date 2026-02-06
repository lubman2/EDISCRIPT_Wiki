EDI Script - (c) EDICOM s.r.o.

# CONVTEXT

converts text in string variable according a conversion file. The conversion file
        has 128 bytes. The function converts all characters great then 127 according this
        table. The flag is set if error happens.

### Format:

## CONVTEXT $a f

a string register f file name

### Example:

LET $0="ěščřžýáíé"

        CONVTEXT $0 "DOStoWIN.cnv"

### See also:

[CONVFILE](CONVFILE.md)
