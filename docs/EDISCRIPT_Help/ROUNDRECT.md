EDI Script - (c) EDICOM s.r.o.

# ROUNDRECT

draws rounded rectangle. The style of the line to use is specified with the PEN
        instruction, color to use as background of the rectangle can be specified by using
        the BRUSH keyword.

### Format:

## ROUNDRECT l t r b w h

l left coordinate of rectangle t top coordinate of rectangle b bottom coordinate of rectangle l left coordinate of rectangle w width of ellipse used to draw rounded corners h height of ellipse used to draw rounded corners

### Example:

PRINTOPEN

        BRUSH 127 127 127 ; gray brush

        ROUNDRECT 10 10 200 100 10 10

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[RECTANGLE](RECTANGLE.md)

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)
