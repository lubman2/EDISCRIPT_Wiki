EDI Script - (c) EDICOM s.r.o.

# XMLTEXTSET

writes a text in a XML document in place where is a pointer. The flag is set on
        if an error happens.

### Format:

## XMLTEXTSET @a t

a XML file pointer number (0 or 1) t string or string variable with text to write in XML document

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLTAG @0 "item,0"

        XMLTEXTSET @0 "Test"

        ...

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLTAG](XMLTAG.md)

[XMLTEXTGET](XMLTEXTGET.md)
