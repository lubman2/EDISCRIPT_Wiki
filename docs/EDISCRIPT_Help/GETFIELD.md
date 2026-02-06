EDI Script - (c) EDICOM s.r.o.

# GETFIELD

reads one item form segment read by function READSEG.

### Format:

## GETFIELD s d ele sub

s source string register d destination string register ele element sub subelement

### Example:

FILEOPEN "test.txt"

        ...

        READSEG $L

        GETFIELD $L $0 2 1

        ...

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READSEG](READSEG.md)
