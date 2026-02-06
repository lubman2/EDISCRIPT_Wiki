EDI Script - (c) EDICOM s.r.o.

# FINDFILE

find file in specified path. The path is specified by FINDPATH. The function set
        a flag if file not found.

### Format:

## FINDFILE p

p string register for file name

### Example:

FINDPATH "c:\test\*.edi"

        LABEL FindFile

        FINDFILE $0

        IF F THEN End

        ;

        GOTO FindFile

        LABEL End

### See also:

[FINDPATH](FINDPATH.md)
