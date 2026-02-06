EDI Script - (c) EDICOM s.r.o.

# TEXTR

prints a text in limited rectangle. Color of text can be set by instruction TEXTCOLOR. Default color is
        black. Font of the text can be specified by instruction FONT. For alignment can
        be used instruction TEXTALIGN.

### Format:

## TEXTR x y a b t

x, y coordinates a, b max size of the text t text

### Example:

PRINTOPEN

        TEXTR 10 10 60 40 "Hello"

        PRINT

        PRINTCLOSE

### See also:

[TEXT](TEXT.md)

[TEXTALIGN](TEXTALIGN.md)

[TEXTCOLOR](TEXTCOLOR.md)

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)
