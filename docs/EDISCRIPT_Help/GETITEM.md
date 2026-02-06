EDI Script - (c) EDICOM s.r.o.

# GETITEM

reads one item from line from file opened by function FILEOPEN separated by any separator.

### Format:

## GETITEM s d col sep

s source string register d destination string register col column to read sep one character for separator

### Example:

FILEOPEN "test.txt"

        ...

        READLINE $L

        GETITEM $L $0 2 ;

        ...

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READSEG](READSEG.md)

[GETTEXT](GETTEXT.md)
