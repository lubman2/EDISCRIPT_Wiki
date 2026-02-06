EDI Script - (c) EDICOM s.r.o.

# EXCELGET

reads value from specified cell. The excel file must be opened by function EXCELOPEN.

### Format:

## EXCELGET s v

s string with cell description v string register for value to put from a cell

or

## EXCELGET r c v

r number of row c number of column v string register for value to put from a cell

### Example:

EXCELOPEN "c:\mydir\test.xls"

        EXCELGET "A1" $0

        EXCELGET 1 1 $0

        EXCELCLOSE

### See also:

[EXCELOPEN](EXCELOPEN.md)

[EXCELCLOSE](EXCELCLOSE.md)

[EXCELSET](EXCELSET.md)

[EXCELSHEET](EXCELSHEET.md)

[EXCELSAVE](EXCELSAVE.md)
