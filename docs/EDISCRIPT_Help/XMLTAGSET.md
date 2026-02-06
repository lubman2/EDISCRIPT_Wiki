EDI Script - (c) EDICOM s.r.o.

# XMLTAGSET

creates new tag in a XML document in place where is pointer The flag is set on if
        an error happens.

### Format:

## XMLTAGSET @a tag

a XML file pointer number (0 or 1) tag string or string variable with tag name

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLTAG @0 "item,0"

        XMLTAGSET @0 "mytag"

        ...

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLTAG](XMLTAG.md)
