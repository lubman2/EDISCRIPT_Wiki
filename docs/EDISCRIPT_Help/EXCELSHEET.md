EDI Script - (c) EDICOM s.r.o.

# EXCELSHEET

selects an excel sheet. The excel file must be opened by function EXCELOPEN.

### Format:

## EXCELSHEET n

n number of sheet to select (1, 2, 3, ...)

### Example:

EXCELOPEN "c:\mydir\test.xls"

        EXCELSHEET 2

        EXCELGET "A1" $0

        EXCELCLOSE

### See also:

[EXCELOPEN](EXCELOPEN.md)

[EXCELCLOSE](EXCELCLOSE.md)

[EXCELGET](EXCELGET.md)

[EXCELSET](EXCELSET.md)

[EXCELSAVE](EXCELSAVE.md)
