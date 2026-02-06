EDI Script - (c) EDICOM s.r.o.

# XMLROOTTAG

retrieves root tag of a XML document. The flag
        is set on if an error happens.

### Format:

## XMLROOTTAG @a $t

a XML file pointer number (0 or 1) t number of string variable for retrieving text

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        LASTERROR $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLROOTTAG @0 $0

        ...

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLTAG](XMLTAG.md)

[XMLTEXTSET](XMLTEXTSET.md)

[XMLTEXTGET](XMLTEXTGET.md)
