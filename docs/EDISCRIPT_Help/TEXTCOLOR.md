EDI Script - (c) EDICOM s.r.o.

# TEXTCOLOR

set color for instruction TEXT.

### Format:

## TEXTCOLOR r g b

r red color of text in range 0-255 g green color of text in range 0-255 b blue color of text in range 0-255

### Example:

PRINTOPEN

        TEXTCOLOR 0 0 255 ; blue

        TEXT 10 10 "Hello"

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[TEXT](TEXT.md)

[TEXTALIGN](TEXTALIGN.md)

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)
