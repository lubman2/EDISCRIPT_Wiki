EDI Script - (c) EDICOM s.r.o.

# XMLSAVE

saves a XML document to a specified file. The flag is set on if an error happens.

### Format:

## XMLSAVE @x f

x XML file pointer number (0 or 1) f file name to save XML document

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        ...

        XMLSAVE @0 "c:\test\my.xml"

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLCLOSE](XMLCLOSE.md)
