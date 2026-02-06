EDI Script - (c) EDICOM s.r.o.

# FINDPATH

set a path for finding files in specified path. A fuction FINDFILE returns then
        file name.

### Format:

## FINDPATH p

p path for finding files

### Example:

FINDPATH "c:\test\*.edi"

        LABEL FindFile

        FINDFILE $0

        IF F THEN End

        ;

        GOTO FindFile

        LABEL End

### See also:

[FINDFILE](FINDFILE.md)
