EDI Script - (c) EDICOM s.r.o.

# FONT

prepare font for function TEXT. First two parameters are mandatory.

### Format:

## FONT "Name",Height,Width,Weight,Type,Escapement

Name name of font Height height of font Width width of font, default is 0 Weight weight of font in ranch 0-9 Type type: 0 - normal; 1 - italic; 2 - underline; 3 - strikeout

### Example:

PRINTOPEN

        FONT "Arial",20

        TEXT 100 30 "Example"

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINTCLOSE](PRINTCLOSE.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)
