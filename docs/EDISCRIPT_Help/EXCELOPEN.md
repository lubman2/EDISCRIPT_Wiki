EDI Script - (c) EDICOM s.r.o.

# EXCELOPEN

opens an excel file (.xls) for reading and writing. The excel file must be closed
        by function EXCELCLOSE.

        NOTE: If the function does not work in service try to create directory for Windows x64:

        C:\Windows\SysWOW64\config\systemprofile\Desktop

        or for Windows x86:

        C:\Windows\System32\config\systemprofile\Desktop

### Format:

## EXCELOPEN f

f string register

### Example:

EXCELOPEN "c:\mydir\test.xls"

        EXCELGET "A1" $0

        EXCELCLOSE

### See also:

[EXCELCLOSE](EXCELCLOSE.md)

[EXCELGET](EXCELGET.md)

[EXCELSET](EXCELSET.md)

[EXCELSHEET](EXCELSHEET.md)

[EXCELSAVE](EXCELSAVE.md)
