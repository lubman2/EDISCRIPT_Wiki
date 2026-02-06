EDI Script - (c) EDICOM s.r.o.

# FILEOPEN

opens text file for reading with function READTEXT or READSEG. The flag is set if
        error happens.

### Format:

## FILEOPEN f

f file name

### Example:

FILEOPEN "test.txt"

        READSEG $L

        GETFIELD $L $0 2 1

        FILECLOSE

### See also:

[FILECLOSE](FILECLOSE.md)

[READLINE](READLINE.md)

[READSEG](READSEG.md)

[GETFIELD](GETFIELD.md)
