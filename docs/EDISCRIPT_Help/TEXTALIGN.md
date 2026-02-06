EDI Script - (c) EDICOM s.r.o.

# TEXTALIGN

set alignment for an instruction TEXT.

### Format:

## TEXTALIGN a

x type of alignment: LEFT, RIGHT, CENTER

### Example:

PRINTOPEN

        TEXTALIGN RIGHT

        TEXT 10 10 "Hello"

        PRINT

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[TEXT](TEXT.md)

[TEXTCOLOR](TEXTCOLOR.md)
