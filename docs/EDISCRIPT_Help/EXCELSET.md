EDI Script - (c) EDICOM s.r.o.

# EXCELSET

sets value in specified cell. The excel file must be opened by function EXCELOPEN.
        Format: c v r c v Example: See also: All right reserved

### Format:

## EXCELSET s v

s string with cell description v string for value to put in a cell

or

## EXCELSET r c v

r number of row c number of column v string for value to put in a cell

### Example:

EXCELOPEN "c:\mydir\test.xls"

        EXCELSET "A1" "Test"

        EXCELSET 1 1 "Test"

        EXCELSAVE

        EXCELCLOSE

### See also:

[EXCELOPEN](EXCELOPEN.md)

[EXCELCLOSE](EXCELCLOSE.md)

[EXCELGET](EXCELGET.md)

[EXCELSHEET](EXCELSHEET.md)

[EXCELSAVE](EXCELSAVE.md)
