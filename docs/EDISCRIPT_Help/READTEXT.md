EDI Script - (c) EDICOM s.r.o.

# READTEXT

reads specified number of characters from file opened by function FILEOPEN.

### Format:

## READTEXT r n

r string register n number of chracters to read

### Example:

FILEOPEN "test.txt"

        READTEXT $L 128

        GETTEXT $L $0 20 10

        FILECLOSE

### See also:

[FILEOPEN](FILEOPEN.md)

[FILECLOSE](FILECLOSE.md)

[READSEG](READSEG.md)

[GETTEXT](GETTEXT.md)

[GETITEM](GETITEM.md)
