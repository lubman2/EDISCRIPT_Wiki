EDI Script - (c) EDICOM s.r.o.

# CONVFILE

converts file according a convert file. The convert file has 128 bytes. The function
        converts all characters great then 127 according this table. The flag is set if
        error happens.

### Format:

## CONVFILE file conv

file file name witch content to convert conv conversion file

### Example:

CONVFILE "test.edi" "DOStoWIN.cnv"

### See also:

[CONVTEXT](CONVTEXT.md)
