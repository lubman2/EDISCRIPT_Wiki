EDI Script - (c) EDICOM s.r.o.

# FILEUNIQUE

creates a unique file name in a selected directory. The file name is created from
        actual date: YYMMDDHHMM.edi.

### Format:

## FILEUNIQUE a $b e

a path for unique name (a first part of a file name) b string register for unique file name e string with extension

### Example:

FILEUNIQUE "c:\mydir" $4 "edi"

### See also:

[FILECOPY](FILECOPY.md)

[RENAME](RENAME.md)
