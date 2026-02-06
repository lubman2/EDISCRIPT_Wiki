EDI Script - (c) EDICOM s.r.o.

# FILEEXIST

sets the flag on if the file does not exist.

### Format:

## FILEEXIST f

f file name

### Example:

CONST Test "test.edi"

        FILEEXIST Test

        IF F THEN err

        EDIREAD @0 Test 1

        ...

        LABEL err

        ...CONST Test "test.edi"

        FILEEXIST Test

        IF F THEN err

        EDIREAD @0 Test 1

        ...

        LABEL err

        ...

### See also:

[FILECOPY](FILECOPY.md)

[FILEDELETE](FILEDELETE.md)

[FILELENGTH](FILELENGTH.md)
