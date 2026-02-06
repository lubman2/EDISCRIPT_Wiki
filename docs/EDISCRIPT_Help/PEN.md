EDI Script - (c) EDICOM s.r.o.

# PEN

prepares pen for functions LINE, RECTANGLE and ROUNDRECT. Default pen is black.

### Format:

## PEN style,width,r,g,b

style 0 - creates a solid pen. 1 - creates a dashed pen. (Valid only when the pen width is 1.) 2 - creates a dotted pen. (Valid only when the pen width is 1.) 3 - creates a pen with alternating dashes and dots. (Valid only when the pen width
                is 1.) 4 - creates a pen with alternating dashes and double dots. (Valid only when the
                pen width is 1.) 5 - creates a null pen. 6 - creates a pen that draws a line inside the frame of closed shapes produced by
                graphics device interface (GDI) output functions that specify a bounding rectangle
                (for example, the RECTANGLE, ROUNDRECT functions). When this style is used with
                GDI output functions that do not specify a bounding rectangle, the drawing area
                of the pen is not limited by a frame. width specifies the pen width, in logical units. If the width member is zero, the pen
                is one pixel r,g,b red, green, blue colors of line in range 0-255

### Example:

PRINTOPEN

        PEN 1 1 255 0 0 ; dashed red pen

        LINE 10 10 100 10"

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)

[BRUSH](BRUSH.md)
