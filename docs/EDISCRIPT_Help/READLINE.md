EDI Script - (c) EDICOM s.r.o.

# READLINE

read one line from file opened by function FILEOPEN.

### Format:

## READLINE r

r string register

### Example:

FILEOPEN "test.txt"

        READLINE $L

        GETTEXT $L $0 20 10

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READSEG](READSEG.md)

[GETTEXT](GETTEXT.md)

[GETITEM](GETITEM.md)
