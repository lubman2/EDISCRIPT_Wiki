EDI Script - (c) EDICOM s.r.o.

# CONST

is a constant in script. Long text or text which is used more then once can be replaced
        with short name of constant. CONST can be placed everywhere in a script file.

### Format:

## CONST name "text"

name alias name for the text text the "name" is replaced by "text"

### Example:

CONST MyFile "c:\mydir\myfile.txt"

        ...

        LET $4="Cannot open file: "+MyFile

### See also:

[LET](LET.md)

[GOTO](GOTO.md)
