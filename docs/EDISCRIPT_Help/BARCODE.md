EDI Script - (c) EDICOM s.r.o.

# BARCODE

prints a barcode.according code 39 specification The ratio of the bar widths can
        range from 2.2:1 to 3:1. To read a barcode reliably the decoder must be able to
        differentiate between the wide and narrow bars. In practice it is better to use
        barcodes close to the 3:1 ratio which allows nearly a 50% barwidth error to occur
        before ambiguity occurs.

### Format:

## BARCODE t x y h w f

t data to display in barcode x left coordinate of barcode y top coordinate of barcode h height of barcode w width of wide line in barcode f width of narrow line in barcode

### Example:

PRINTOPEN

        BARCODE "BO3456789" 100 100 200 20 8 ; ratio 2.5:1

        BARCODE "BO3456789" 100 700 200 24 8 ; ratio 3:1

        PRINTPREVIEW

        PRINTCLOSE

### See also:

[PRINTOPEN](PRINTOPEN.md)

[PRINT](PRINT.md)

[PRINTPREVIEW](PRINTPREVIEW.md)

[PRINTCLOSE](PRINTCLOSE.md)
