EDI Script - (c) EDICOM s.r.o.

# BRUSH

prepares brush. Functions RECTANGLE and ROUNDRECT are filled with selected brush.

### Format:

## BRUSH r g b

r value in range 0-255 for red color g value in range 0-255 for green color b value in range 0-255 for blue color

### Example:

PRINTOPEN

        BRUSH 0 0 255

        RECTANGLE 10 10 200 100 ; blue rectangle

        PRINT

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PEN](PEN.md)

[FONT](FONT.md)
