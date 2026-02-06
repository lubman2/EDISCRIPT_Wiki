EDI Script - (c) EDICOM s.r.o.

# BITMAP

prints a bitmap. A file name of bitmap must be available when document is printed.

### Format:

## BITMAP l t r b f

l left coordinate of bitmap t top coordinate of bitmap r right coordinate of bitmap b bottom coordinate of bitmap f string, constant or string register with file name of bitmap

### Example:

PRINTOPEN

        BITMAP 10 10 200 100 "logo.bmp"

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)
