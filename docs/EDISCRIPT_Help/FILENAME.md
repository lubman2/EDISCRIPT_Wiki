EDI Script - (c) EDICOM s.r.o.

# FILENAME

separates a short file name from a full path name.

### Format:

## FILENAME r $a

r full path file name a string variable for short file name

### Example:

LET $0="c:\mydir\test.edi"

        FILENAME $0 $2 ; "test.edi"

### See also:

[FILEUNIQUE](FILEUNIQUE.md)

[FILEEXIST](FILEEXIST.md)
