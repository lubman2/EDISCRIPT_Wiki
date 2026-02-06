EDI Script - (c) EDICOM s.r.o.

# RENAME

renames a name of the file.

### Format:

## RENAME a b

a old file name b new file name

### Example:

LET $4="c:\mydir\test0.edi"

        RENAME "c:\mydir\test.edi" $4

### See also:

[FILECOPY](FILECOPY.md)

[FILEUNIQUE](FILEUNIQUE.md)
