EDI Script - (c) EDICOM s.r.o.

# GETTEXT

reads a text form string.

### Format:

## GETTEXT s d pos len

s source string register d destination string register pos position to start to read (1, 2, 3, ...) len number of characters to read

### Example:

FILEOPEN "test.txt"

        ...

        READLINE $L

        GETTEXT $L $0 20 10

        ...

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READSEG](READSEG.md)

[GETITEM](GETITEM.md)
