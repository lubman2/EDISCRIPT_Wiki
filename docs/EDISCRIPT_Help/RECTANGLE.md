EDI Script - (c) EDICOM s.r.o.

# RECTANGLE

draws rectangle. The style of the line to use is specified with the PEN instruction,
        color to use as background of the rectangle can be specified by using the BRUSH
        keyword.

### Format:

## RECTANGLE l t r b

l left coordinate of rectangle t top coordinate of rectangle r right coordinate of rectangle b bottom coordinate of rectangle

### Example:

PRINTOPEN

        BRUSH 127 127 127 ; gray brush

        RECTANGLE 10 10 200 100

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[ROUNDRECT](ROUNDRECT.md)

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)
