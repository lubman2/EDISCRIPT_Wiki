EDI Script - (c) EDICOM s.r.o.

# FILEEXT

changes file name extension to new specified extension.

### Format:

## FILEEXT f e

f string register for file name e string with a new extention

### Example:

LET $0="c:\mydir\test.edi"

        FILEEXT $0 "txt" ; result: "c:\mydir\test.txt"

### See also:

[FILENAME](FILENAME.md)
