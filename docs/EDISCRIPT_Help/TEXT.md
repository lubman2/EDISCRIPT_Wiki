EDI Script - (c) EDICOM s.r.o.

# TEXT

prints a text. Color of text can be set by instruction TEXTCOLOR. Default color is
        black. Font of the text can be specified by instruction FONT. For alignment can
        be used instruction TEXTALIGN.

### Format:

## TEXT x y t

x, y coordinates t text

### Example:

PRINTOPEN

        TEXT 10 10 "Hello"

        PRINT

        PRINTCLOSE

### See also:

[TEXTR](TEXTR.md)

[TEXTALIGN](TEXTALIGN.md)

[TEXTCOLOR](TEXTCOLOR.md)

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)
