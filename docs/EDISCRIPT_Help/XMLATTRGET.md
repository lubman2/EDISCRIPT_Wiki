EDI Script - (c) EDICOM s.r.o.

# XMLATTRGET

retrieves a text of specified attribute in a XML document in tag where is pointer.
        The flag is set on if an error happens.

### Format:

## XMLATTRGET @x "a" $t

x XML file pointer number (0 or 1) a attribute name t number of string variable for retrieving text

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLTAG @0 "item,0"

        XMLATTRGET @0 "Attr" $0

        ...

        XMLCLOSE @0

### See also:

[XMLTAG](XMLTAG.md)

[XMLTEXTSET](XMLTEXTSET.md)

[XMLTEXTGET](XMLTEXTGET.md)

[XMLATTRSET](XMLATTRSET.md)
