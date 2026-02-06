EDI Script - (c) EDICOM s.r.o.

# XMLOPEN

opens an XML file in memory. The flag is set on if an error happens. A function
        XMLERROR returns a text of an error.

### Format:

## XMLOPEN @a f

a XML file pointer number (0 or 1) f string, string variable or constant with file name to open

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        XMLERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        ...

        XMLCLOSE @0

### See also:

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLROOTTAG](XMLROOTTAG.md)
