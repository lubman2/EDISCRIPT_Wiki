EDI Script - (c) EDICOM s.r.o.

# EXCELCLOSE

closes an opened excel file (.xls). The excel file can be opend by EXCELOPEN function.

### Format:

## EXCELCLOSE

no parameters

### Example:

EXCELOPEN "c:\mydir\test.xls"

        EXCELGET "A1" $0

        EXCELCLOSE

### See also:

[EXCELOPEN](EXCELOPEN.md)

[EXCELGET](EXCELGET.md)

[EXCELSET](EXCELSET.md)

[EXCELSHEET](EXCELSHEET.md)

[EXCELSAVE](EXCELSAVE.md)
