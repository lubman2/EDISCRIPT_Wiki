EDI Script - (c) EDICOM s.r.o.

# PRINTOPEN

opens print buffer. The buffer is need for printing. All print must start with this
        instruction and terminate with instruction PRINTCLOSE.

### Format:

## PRINTOPEN

no parameters

### Example:

PRINTOPEN

        TEXT 200 100 "Hello world"

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PAGE](PAGE.md)
