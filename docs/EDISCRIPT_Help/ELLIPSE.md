EDI Script - (c) EDICOM s.r.o.

# ELLIPSE

prints ellipse. A PEN can change margin and a BRUSH can change inside of ellipse.

### Format:

## ELLIPSE l t r b

l left coordinate for ellipse t top coordinate for ellipse r right coordinate for ellipse b bottom coordinate for ellipse

### Example:

PRINTOPEN

        BRUSH 0 0 255

        PEN 255 0 0

        ELLIPSE 10 10 200 100

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PEN](PEN.md)

[BRUSH](BRUSH.md)
