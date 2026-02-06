EDI Script - (c) EDICOM s.r.o.

# READSEG

reads one EDI segment from the file opened by function FILEOPEN.

### Format:

## READSEG r

f string register

### Example:

FILEOPEN

        READSEG $L

        GETFIELD $L $0 2 1

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READLINE](READLINE.md)

[GETITEM](GETITEM.md)
