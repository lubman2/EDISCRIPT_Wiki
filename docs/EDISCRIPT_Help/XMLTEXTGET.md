EDI Script - (c) EDICOM s.r.o.

# XMLTEXTGET

reads text in a specified tag in a XML document in place where is pointer. The flag
        is set on if an error happens.

### Format:

## XMLTEXTGET @a $t

a XML file pointer number (0 or 1) t number of string variable for retrieving text

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLTAG @0 "item,0"

        XMLTEXTGET @0 $0

        ...

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLTAG](XMLTAG.md)

[XMLTEXTSET](XMLTEXTSET.md)
