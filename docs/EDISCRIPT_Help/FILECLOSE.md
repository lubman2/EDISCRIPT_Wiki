EDI Script - (c) EDICOM s.r.o.

# FILECLOSE

closes the file opened by function FILEOPEN.

### Format:

## FILECLOSE

no parameters

### Example:

FILEOPEN "text.txt"

        ...

        READSEG $L

        GETFIELD $L $0 2 1

        ...

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[READLINE](READLINE.md)

[READSEG](READSEG.md)
